# Field Types and Valid Values #

This page explains how the various records and sections in the CCADB are
best filled out, with some advice on how to create or obtain the data.
<br><br>
Table of Contents:
1. [Audit Information](fields#audit-information)
2. [Auditor Information](fields#auditor-information)
3. [Formula Fields](fields#formula-fields)
4. [PEM Data](fields#pem-data)
5. [Policies and Practices Information](fields#policies-and-practices-information)
6. [Revocation Information](fields#revocation-information)
7. [Uploading Documents](fields#uploading-documents)

## Audit Information ##

<table border="1">
<tr valign="top"><th>Field Name</th><th>What to Enter</th></tr>

<tr valign="top">
<td>Audits Same as Parent </td>
<td> Check this box if this certificate has the same audit information as the
issuing certificate (or a subset). If you check this box, then do not enter
data into the other fields in this section. If you need to add data to the
other fields in this section, then uncheck this box.</td>
</tr>
</table>
<br>
There are 5 audit statements that may be provided:
<ol>
<li>Standard Audit</li>
<li>Code Signing Audit</li>
<li>BR Audit</li>
<li>EV SSL Audit</li>
<li>EV Code Signing Audit</li>
</ol>
For each applicable audit, the following information must be provided, and must meet 
the individual Root Store requirements and the requirements of 
[section 5.1 of the CCADB Policy][CCADB-Policy].
<table border="1">
<tr valign="top"><th>Field Name</th><th>What to Enter</th></tr>

<tr valign="top">
<td>Audit</td>
<td>URL to the audit statement PDF. <br>
WebTrust Seals: Enter the WebTrust Seal URL into this field. When you save your changes, the CCADB will automatically convert the Seal URL to the URL of the corresponding audit statement PDF.
</td>
</tr>
<tr valign="top">
<td>Audit Type </td>
<td> Choose one of the provided options that most closely aligns with the type of audit;
e.g. WebTrust or ETSI EN 319 411.
</td>
</tr>
<tr valign="top">
<td>Audit Statement Date </td>
<td>Date that the audit statement was signed.</td>
</tr>
<tr valign="top">
<td>Audit Period Start Date <br>
Audit Period End Date</td>
<td>In a period‐of‐time audit, the Audit Period is the period
between the first day (start) and the last day of operations (end) covered by
the auditors in their engagement. (This is not the same as the period of time 
when the auditors are on-site at the CA.)
<br>
The period during which the CA issues certificates SHALL be divided into an
unbroken sequence of audit periods. An audit period MUST NOT exceed one year
in duration.
</td>
</tr>

</table>

<br>

## Auditor Information ##

<table border="1">
<tr valign="top"><th>Field Name</th><th>What to Enter</th></tr>

<tr valign="top">
<td>Auditor </td>
<td> Find all Auditors known to the CCADB by clicking on the 'Auditors' report
in the 'Custom Links' section in any root certificate, intermediate certiifcate, 
or case page. Contact your Root Store Operator if your auditor is not in this list. 
<br>
To fill in the auditor's name, click on the pencil icon in the 'Auditor' field, 
then enter a string of two or more characters that you expect to be in your 
auditor's name and hit 'Return'. Click on your auditor's name, then
click on the 'Save' button. 
</td>
</tr>
<tr valign="top">
<td>Auditor Location </td>
<td> Find all Auditor Locations known to the CCADB by clicking on the 'Auditors' report
in the 'Custom Links' section in any root certificate, intermediate certiifcate, 
or case page. Contact your Root Store Operator if your auditor's location is not in this list. 
<br>
To fill in the auditor's location, click on the pencil icon in the 'Auditor Location' field,
then enter a string of two or more characters that you expect to be in your 
auditor's location and hit 'Return'. Click on your auditor's location, then
click on the 'Save' button. 
 </td>
</tr>
</table>

<br>
Auditor qualifications are verified and entered into the CCADB by a Root Store Operator. 
For example, Mozilla re-verifies auditor qualifications annually as described
 [here][Auditor-Qualifications].
 
 Note: The CCADB considers the terms "intermediate" and "subordinate" synonymous.

## Formula Fields ##
These are some of the fields that are automatically filled in by the CCADB and cannot be manually edited.

<table border="1">
<tr valign="top"><th>Field Name</th><th>Logic</th><th>Updates</th></tr>
<tr valign="top">
<td>Derived Trust Bits </td>
<td>
<ul>
<li>Set to empty when the certificate is expired or revoked.</li>
<li>Directly map to Extended Key Usage (EKU) values when the certificate's EKU is present and not empty. </li>
 <li> If the EKU is empty or not present, then set "Derived Trust Bits" to the union of the trust-bits/EKUs that are on the parent root certificate for each root store that it is included in. 
 <ul>
 <li> Check for doppelganger (same Subject+SPKI) root certificates, and if found, update the union to add the trust-bits/EKUs that are on the parent root certificate for each root store that it is included in (if not already in the union). </li>
</ul>
</li>
 </ul>
 <ul>
 <li> If this certificate has an intermediate certificate as its parent in the CCADB, then:
 <ul>
 <li> Create "List2" that consists of the parent certificate’s "Derived Trust Bits" unioned with the "Derived Trust Bits" of all of the parent certificate’s unexpired unrevoked doppelganger (same Subject+SPKI) certificates. </li>
 <li> Remove anything from this certificate's "Derived Trust Bits" that is not in "List2".</li>
 </ul>
 </li>
</ul>
</td>
<td> 
When related fields are updated on a root or intermediate certificate record, a trigger method launches an asynchronous process that updates this field (if needed) for every certificate within that record's CCADB hierarchy.
 </td> 
</tr>
<tr valign="top">
<td>EV SSL Capable </td>
<td> 
<ol>
For an intermediate certificate to be considered technically capable of issuing EV SSL certificates, all of the following have to be true for that certificate as well as the intermediate certificates that it chains up to.
<li> The certificate is not revoked and not expired.</li>
<li> "Derived Trust Bits" field contains "Server Authentication" </li>
<li> The root certificate that it chains up to is enabled for EV by at least one of the root stores that it is included in. </li>
<li> "Policy Identifiers" field contains one or more of 2.23.140.1.1, 2.5.29.32.0, or any of the values in the ExtendedValidation.cpp OIDs field of the root certificate. </li>
</ol> 
If the above check fails for a parent intermediate certificate, then look for doppelganger (same Subject+SPKI, not expired, not revoked) certificates and perform the check on any that are found.
</td>
<td>
When related fields are updated on a root or intermediate certificate record, a trigger method launches an asynchronous process that updates this field (if needed) for every certificate within that record's CCADB hierarchy.
</td> 
</tr>
<tr valign="top">
<td>Technically Constrained </td>
<td> 
<ul>
<li> Set to FALSE if the certificate does not contain an Extended Key Usage (EKU) extension. </li>
<li> Set to TRUE if the EKU does not contain id‐kp‐serverAuth or anyExtendedKeyUsage. </li>
<li> If the EKU contains id‐kp‐serverAuth, then set to TRUE if the certificate includes the Name Constraints X.509v3 extension with constraints on dNSName, iPAddress and DirectoryName. Otherwise set to FALSE. </li>
</ul>
  </td>
<td> Set when certificate PEM is imported into the CCADB. </td> 
</tr>
<tr valign="top">
<td>Has Non-constrained Doppelganger?</td>
<td>This field is set to TRUE when its "Technically Constrained" field is set to TRUE and there are doppelganger (same Subject+SPKI, not expired, not revoked) intermediate certificates that have Technically Constrained == FALSE. </td>
<td> A batch program runs once per day to update this flag. </td> 
</tr>

</table>

<br>
 
## PEM Data ##

The CCADB accepts certificate information in the [PEM][PEM] format. PEM is a
container format defined in RFCs [1421][RFC-1421] to [1424][RFC-1424]. PEM
actually means Privacy Enhanced Mail, but the container format it uses is a
Base64 translation of [X.509][X509] [ASN.1][ASN1] keys.

For reference, here are a few OpenSSL commands that convert certificates 
from other formats into PEM.
* openssl pkcs7 -in certificates.p7b -print_certs -out certificates.pem
* openssl pkcs12 -in certificates.pfx -out certificates.pem -nodes
* openssl x509 -inform der -in certificate.der -out certificate.pem

You may use the [Certificate Viewer][certViewer] to verify that your 
certificate is in the correct PEM format.

## Policies and Practices Information ##

<table border="1">
<tr><th>Field Name</th><th>What to Enter</th></tr>
<tr valign="top" align="left">
<td>CP/CPS Same as Parent</td>
<td>Check this box if this certificate has the same CP/CPS information as the
issuing certificate (or a subset). If you check this box, then do not enter
data into the other fields in this section. If you need to add data to the
other fields in this section, then uncheck this box.</td>
</tr>
<tr valign="top" align="left">
<td>Policy Documentation</td>
<td>Notes about the documentation, such as which language the documents are
in, or additional documents that need to be listed.</td>
</tr>
<tr valign="top" align="left">
<td>CA Document Repository</td>
<td>URL to the document repository pertaining to this certificate.</td>
</tr>
<tr valign="top" align="left">
<td>Certificate Policy (CP)</td>
<td>URL to the Certificate Policy (CP) pertaining to this certificate.</td>
</tr>
<tr valign="top" align="left">
<td>Certificate Practice Statement</td>
<td>URL to the Certificate Practice Statement (CPS) pertaining to this
certificate.</td>
</tr>
</table>

<br>

## Revocation Information ##
### Revocation Information For This Certificate ###

<table border="1">
<tr valign="top"><th>Field Name</th><th>What to Enter</th></tr>
<tr valign="top">
<td>Revocation Status </td>
<td> The CCADB Policy, says “If a subordinate CA certificate is revoked, the CCADB must be updated to mark it as revoked, including the reason for revocation, within seven calendar days of revocation.” 
</td>
</tr>
<tr valign="top">
<td>Date of Revocation </td>
<td> Must match the revocation date indicated in the CRL.
 </td>
</tr>
<tr valign="top">
<td>RFC 5280 Revocation Reason Code</td>
<td> Must match the revocation reason code indicated in the CRL.
 </td>
</tr>
<tr valign="top">
<td>Alternate CRL</td>
<td> Only fill in this field when this certificate does not contain a CRL URL. Note that the BRs require intermediate certificates to contain CRL URLs.
 </td>
</tr>
</table>

<br>

### Pertaining to Certificates Issued by this CA ###
<table border="1">
<tr valign="top"><th>Field Name</th><th>What to Enter</th></tr>
<tr valign="top">
<td>Full CRL Issued By This CA</td>
<td> Enter the URL to the full CRL for certificates issued by this CA.
</td>
</tr>
<tr valign="top">
<td>JSON Array of Partitioned CRLs</td>
<td> When there is no full CRL for certificates issued by this CA, provide a JSON array whose elements are URLs of partitioned, DER-encoded CRLs that when combined are the equivalent of a full CRL for certificates issued by this CA. The JSON array may omit obsolete partitioned CRLs whose scopes only include expired certificates.
<br><br>
Example:
<br>
&#91; "http://cdn.example/crl-1.crl", "http://cdn.example/crl-2.crl" &#93;
<br>
 </td>
</tr>
</table>

<br>


## Uploading Documents ##

Many CCADB fields require URLs to documents. In general, CP/CPS and Audit
information should be provided on the CA Owner's website, subordinate CA Owner's website, or the auditor's website.
However, if for some reason this is not possible, you can use the
Bugzilla bug-tracking system to store the documents and get a URL for use in
the CCADB as follows:

1. If you don't already have a Bugzilla account, [create one][BZ-Create-Acct]
   for yourself.
2. [Search][BZ-Doc-Bugs] to see if there is already a Bugzilla Bug for your CA
   that you can attach your documents to.
3. If one does not exist for your CA, [create one][BZ-Create-Bug].
   * Enter Summary as: "Documents for &lt;your CA's name&gt;"
   * Enter Description as: "The purpose of this bug is to store documents
     related to the root and intermediate certificates
     for &lt;your CA's name&gt;."
4. Attach the document to the bug using the attachment mechanism.
5. Copy and paste the link to the attachment into the corresponding field in
   the CCADB.
6. Repeat steps 4 and 5 as needed, using the same Bugzilla bug.


[Auditor-Qualifications]: https://wiki.mozilla.org/CA/Audit_Statements#Auditor_Qualifications
[CCADB-Policy]:  https://www.ccadb.org/policy#51-audit-statement-content
[PEM]:            https://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions
[RFC-1421]:       https://tools.ietf.org/html/rfc1421
[RFC-1424]:       https://tools.ietf.org/html/rfc1424
[X509]:           https://en.wikipedia.org/wiki/X.509
[ASN1]:           https://en.wikipedia.org/wiki/Abstract_Syntax_Notation_One
[certViewer]:   https://certviewer-dot-ccadb-231121.appspot.com/certviewer
[BZ-Create-Acct]: https://bugzilla.mozilla.org/createaccount.cgi
[BZ-Doc-Bugs]:    https://bugzilla.mozilla.org/buglist.cgi?&query_format=advanced&component=CA%20Documents&product=CA%20Program
[BZ-Create-Bug]:  https://bugzilla.mozilla.org/enter_bug.cgi?&component=CA%20Documents&product=CA%20Program
