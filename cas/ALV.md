# Audit Letter Validation (ALV) #

The CCADB uses an Audit Letter Validation (ALV) tool that is provided by Microsoft to automatically parse and validate audit statements. The ALV eliminates manual processing, but it requires audit statements to follow some basic rules in order to function properly. If an audit statement fails to meet any of the [Audit Statement Requirements and Format Rules](../policy#51-audit-statement-content), the CA will be asked to work with their auditor to provide an audit statement that passes ALV.

## Root Certificates ##

CAs are required to update the audit, CP, CPS and test website information for their certificate hierarchies at least annually. To provide this information for root certificates, create one [Audit Case](updates#audit-case-workflow) in the CCADB for a particular set of audits (e.g. Standard Audit, BR audit, EV SSL Audit, Code Signing Audit).
* [Update audit, CP, CPS, and testwebsite information in the CCADB ](updates)
* [Common ALV Findings](ALV#common-alv-findings)

## Intermediate Certificates ##

Subordinate CAs who operate non-technically-constrained intermediate certificates have the keys to the internet just as much as the CAs who have root certificates directly included in a browser root store. Meaning that such subordinate CAs can also issue TLS certificates for any website or domain, so it is imperative that the same rules are being followed by all subordinate CAs operating non-technically-constrained intermediate certificates. There are currently about 150 root certificates in browser root stores, which leads to about 3,000 intermediate certificates that are trusted by browser root stores. To help enforce the rules at the intermediate certificate level, CCADB participants require disclosure of non-technically-constrained intermediate certificates. CCADB automatically runs ALV on the intermediate certificate records and reports the results to CAs and root store operators in their CCADB home pages.

CAs are required to annually update the audit and CP/CPS for their non-technically-constrained intermediate certificates chaining to root certificates included in browser root stores. To provide this information for intermediate certificates, directly update the corresponding record in the CCADB then click on the "Audit Letter Validation [ALV]" button. 

When the audit statements for an intermediate certificate are the same as the certificate that signed it, check the “Audits Same as Parent” checkbox instead of providing separate audit information. When the "Audits Same as Parent" field is checked for an intermediate certificate record, the CCADB will look up the parent chain until audit statements are found, and then run ALV using those audit statements. When the "Audits Same as Parent" field is not checked, the CCADB will directly pass the audit statements in the intermediate certificate record into ALV.

The following fields are set by running ALV on an intermediate certificate record in the CCADB. CAs may cause ALV to be run on the record by clicking on the "Audit Letter Validation [ALV]" button. Additionally CCADB has automated processes that will regularly check for intermediate certificate records that need to have ALV run.

* Standard Audit ALV Found Cert
    * This field will be set to PASS when ALV finds the SHA-256 Fingerprint for that certificate in the standard audit statement
* BR Audit ALV Found Cert
    * This field will only be set when the [Derived Trust Bits](fields#formula-fields) field has "Server Authentication" in its list. 
    * This field will be set to PASS when ALV finds the SHA-256 Fingerprint for that certificate in the BR audit statement. 
* EV SSL Audit ALV Found Cert
    * This field will only be set when the [Derived Trust Bits](fields#formula-fields) field has "Server Authentication" in its list, and the [EV SSL Capable](fields#formula-fields) field is set to TRUE. 
    * This field will be set to PASS when ALV finds the SHA-256 Fingerprint for that certificate in the EV SSL audit statement.

When ALV returns FAIL for "Standard Audit ALV Found Cert", "Code Signing Audit ALV Found Cert", "BR Audit ALV Found Cert", or "EV SSL Audit ALV Found Cert" for one of your CA's intermediate certificate records in the CCADB, do the following.

* Check the corresponding audit statement to make sure the SHA-256 fingerprint of the certificate is correctly listed.
* If the SHA-256 fingerprint is listed in the audit statement, then make sure that it meets the [format specifications](../policy#51-audit-statement-content), such as no colons, no spaces, no line feeds.
* Have your auditor provide an updated audit statement that follows the [formatting requirements](../policy#51-audit-statement-content) for the SHA-256 Fingerprints.
* If you do not agree with the ALV results, add comments to the "Standard Audit ALV Comments", "Code Signing Audit ALV Comments", "BR Audit ALV Comments", or "EV SSL Audit ALV Comments" fields to indicate that the SHA-256 fingerprint is listed correctly in the audit statement.
* If the audit statement is indeed missing the SHA-256 fingerprint for the certificate, then file an [Incident Report](https://wiki.mozilla.org/CA/Incident_Dashboard), and add the link to the Incident Report to one of the "...ALV Comments" fields.

Important clarifications:

* If the CA has a currently valid audit report at the time of creation of the intermediate certificate, then the current audit statement does not need to be updated and the new certificate must appear on the CA's next periodic audit reports.
* Intermediate certificates that contain "Server Authentication" in the [Derived Trust Bits](fields#formula-fields) field are considered to be technically capable of issuing TLS certificates, and they must be listed in the CA’s BR audit report.
* If multiple intermediate certificates with the same Subject + SPKI have been issued, each one must have their SHA-256 Fingerprint listed in appropriate audit statements according to the [Derived Trust Bits](fields#formula-fields) field.
* Cross-Certificates are also considered intermediate certificates, which must also be audited and specifically listed in the applicable audit statements according to the [Derived Trust Bits](fields#formula-fields) field.
* Self-signed certificates that share a Subject and SPKI with a root certificate that is included in a root store are treated by browsers as intermediate certificates because they chain up to an included root, so these certificates must also be listed in the applicable audit statements according to the [Derived Trust Bits](fields#formula-fields) field. 
    * An example of this situation is when an older version of a root certificate exists and a newer version of the root certificate is created. In this case, a valid chain may be constructed as: leaf --> untrusted root --> trusted root. In other words, that "untrusted" root is technically trusted by the root store because it chains to a trusted root, so it's SHA256 fingerprint must also be listed in the applicable audit statements.

Acceptable remediation:
* Have your auditor issue a revised report that includes the intermediate certificate.
    * If the certificate has been in existence for past audit periods, then you must also file an [Incident Report](https://wiki.mozilla.org/CA/Incident_Dashboard).
    * An Incident Report may not be needed if the certificate is self-signed and has the same Subject and SPKI as other certificates listed in the audit statement. For example, this can happen when a root store includes one version of a root certificate, but another version of the root certificate can be part of a valid chain constructed as: leaf --> untrusted root --> trusted root.
* Revoke the intermediate certificate in accordance with root store policies and the BRs.
    * If your CA decides not to revoke the certificate within the timeline specified by section 4.9 of the BRs, then that is another incident, which must be addressed in a separate [Incident Report](https://wiki.mozilla.org/CA/Incident_Dashboard). 

## Common ALV Findings ##
ALV formatting requirements are specified in 
[section 5.1 of the CCADB Policy](../policy#51-audit-statement-content).

<table border="1">
<tr valign="top"><th>ALV Error</th><th>Meaning</th><th>Recommended Action</th></tr>
<tr valign="top">
<td>Thumbprint not found </td>
<td>SHA-256 Fingerprint of the certificate not found in the audit statement. </td>
<td>
<ul>
<li> Check that the SHA-256 fingerprint for the certificate is clearly listed in in the audit  statement and follows the format requirements; e.g. the fingerprint contains no colons, no spaces, no line feeds. </li>
<li> Request an updated audit statement from your auditor that clearly specifies the SHA-256 Fingerprints of each root and intermediate certificate that was in scope of the audit, using the correct format for the fingerprints. </li>
</ul>
</td> 
</tr>
<tr valign="top">
<td>Statement Date Not Found</td>
<td>The audit statement date was not found in the audit statement. </td>
<td>
<ul>
<li>Check that the date that the audit statement was issued is clearly indicated in the audit statement and follows the format requirements for dates.</li>
<li> If needed, request an updated audit statement from your auditor. </li>
<li>Sometimes ALV gives false alerts for dates, so if needed you may add a comment about that in one of the "...ALV Comments" fields.
</li> 
</ul>
</td> 
</tr>
<tr valign="top">
<td>Audit Period Not Found </td>
<td>ALV was unable to find the audit period start and end dates in the audit statement. </td>
<td>
<ul>
<li> Check that the audit period dates in the audit statement match the format requirements. </li>
<li> If the dates in the audit statement follow the format requirements, then this error can also be the result of the audit period being stated in various locations throughout the document or separately in different rows within a table, etc. </li>
<li>It helps ALV for the audit period to be stated towards the top of the document </li>
<li> You may see this error if there are other problems with the audit period, such as it being less than one month -- point-in-time audits have to be manually reviewed. </li>
</ul>
</td> 
</tr>
<tr valign="top">
<td>Failed to validate EKU ... because the standard names and standard policies are not found in the audit letters </td>
<td>ALV was unable to find the specific text (case insensitive) that it looks for for each EKU. For example, "319 411-1 v1.1.1, dvcp;ovcp;ptc-br" </td>
<td>Make sure that the audit statement correctly indicates the audit criteria that was used, and that it satisfies root store requirements.
The following are xamples of the policy information that ALV looks for, depending on the EKU's or Trust Bits that each root store has applied to the root certifiate, and the "Derived Trust Bits" for an intermediate certificate.
<ul>
<li> ETSI EN 319 411-1 V1.2.2, LCP;DVCP </li>
<li> ETSI EN 319 411-1 V1.2.2, LCP;OVCP;EVCP </li>
<li> ETSI EN 319 411-1 V1.2.2, NCP;EVCP </li>
<li> ETSI EN 319 411-1 V1.2.2, NCP;NCP+ </li>
<li> ETSI EN 319 411-2 V2.2.2, QCP-w </li>
<li> ETSI EN 319 411-2 V2.2.2, QCP-w; EVCP </li>
<li> ETSI EN 319 411-2 V2.2.2, QCP-l;QCP-l-qscd;QCP-n;QCP-n-qscd </li>
<li> Principles and Criteria for Certification Authorities - Version 2.2.1 </li>
<li> WebTrust Principles and Criteria for Certification Authorities – SSL Baseline with Network Security v2.5 </li>
<li> WebTrust Principles and Criteria for Certification Authorities - Extended Validation SSL v1.7.3 </li>
</ul>
</td> 
</tr>
<tr valign="top">
<td>Auditor Not Found </td>
<td>ALV was unable to find the specified auditor name in the audit statement </td>
<td>
<ul>
<li> Ensure the correct Auditor is selected in the record and that it matches the auditor name recorded in your audit statement. </li> 
<li> If both look correct ask a root store manager to update the auditor's information in the CCADB. </li>
</ul>
</td> 
</tr>
<tr valign="top">
<td>CA Owner Not Found </td>
<td>ALV was unable to find the CA Owner's name (as specified in the CCADB) in the audit statement. For intermediate certificate records with their own audit statements this will be the value in the "Subordinate CA Owner" field </td>
<td>
<ul>
<li> Check that your CA Name in the CCADB is correct and that your CA Name specified in the Audit Letter is correct. </li>
<li> For Audit Cases with this problem, you may ask a root store manager to update your CA Owner Name. </li>
<li> For intermediate certificates with their own audit statements, you should update the "Subordinate CA Owner" field directly to match the CA name in the audit statement. </li>
</ul>
</td> 
</tr>
<tr valign="top">
<td>Download Audit Letter Fail </td>
<td>The provided link to the audit statement did not work. </td>
<td>Correct and test the audit statement links in the CCADB record then try again.</td> 
</tr>
<tr valign="top">
<td>Audit Letter Not Found In Certain Location </td>
<td>ALV contains a list of known audit locations, such as auditor websites and cpacanada.ca. This error will be given when the URL to the audit statement does not match any of the URLs in the known audit locations. </td>
<td>
<ul>
<li> If you are testing the preliminary audit statement, then you may ignore this error. </li>
<li> Make sure that the URL that you entered into the CCADB is https. </li>
<li> If you are running ALV on the final audit statement, then this error should not happen unless the audit statement is qualified (WebTrust) or the ETSI Certificate was not issued. </li>
<li> In those situations the root store operator will need to contact the auditor, so it will help if you provide the auditor's contact information in a Case Comment. </li>
<li> If the audit statement is on the auditor's website and you are still receiving this error, then ask a root store manager to add the auditor's website to the list of known audit locations for ALV. </li>
</ul>
</td> 
</tr>
<tr valign="top">
<td>Audit Letter Not PDF </td>
<td>ALV was unable to download and parse the document at the audit statement URL.</td>
<td>Update the Audit Statement links in the record to point to a valid PDF file. </td> 
</tr>
</table>
 <br>