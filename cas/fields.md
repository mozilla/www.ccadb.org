# Field Types and Valid Values #

This page explains how the various records and sections in the CCADB are
best filled out, with some advice on how to create or obtain the data.
<br><br>
Table of Contents:
<ol>
<li> Audit Information </li>
<li> Auditor Information </li>
<li> Forumula Fields </li>
<li> PEM Data </li>
<li> Policies and Practices Information </li>
<li> Revocation Information </li>
<li> Uploading Documents </li>
</ol>

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
the root store requirements and the requirements of 
[section 5.1 of the Common CCADB Policy][CCADB-Policy].
<table border="1">
<tr valign="top"><th>Field Name</th><th>What to Enter</th></tr>

<tr valign="top">
<td>Audit</td>
<td>URL to the audit statement PDF. <br>
WebTrust Seals: Enter the WebTrust Seal URL into this field. When you save your changes, the CCADB will automatically convert the Seal URL to  the URL of the corresponding audit statement PDF.
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
the auditors in their engagement.  (This is not the same as the period of time 
when the auditors are on-site at the CA.)
<br>
The period during which the CA issues Certificates SHALL be divided into an
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
in the 'Custom Links' section in any Root Certificate, Intermediate Certiifcate, 
or Case page. Contact your root store operator if your auditor is not in this list. 
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
in the 'Custom Links' section in any Root Certificate, Intermediate Certiifcate, 
or Case page. Contact your root store operator if your auditor's location is not in this list. 
<br>
To fill in the auditor's location, click on the pencil icon in the 'Auditor Location' field,
then enter a string of two or more characters that you expect to be in your 
auditor's location and hit 'Return'. Click on your auditor's location, then
click on the 'Save' button. 
 </td>
</tr>
</table>

<br>
Auditor qualifications are verified and entered into the CCADB by a root store operator. 
For example, Mozilla re-verifies auditor qualifications annually as described
 [here][Auditor-Qualifications].


## Formula Fields ##
These are some of the fields that are automatically filled in by the CCADB and cannot be manually edited.

<table border="1">
<tr valign="top"><th>Field Name</th><th>Logic</th><th>Updates</th></tr>
<tr valign="top">
<td>Derived Trust Bits </td>
<td>
<ul>
<li>TO DO </li>
</ul>
</td>
<td> TO DO </td> 
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
<td> TO DO </td> 
</tr>
<tr valign="top">
<td>Technically Constrained </td>
<td> This is set based on mozillaPolicyV2_5.isTechnicallyConstrained from extracted PEM result.  </td>
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

[Certificate Explainer][Certsplainer] may be used to
convert a certificate in any other format into PEM, as follows:

* Visit the [Certificate Explainer][Certsplainer].
* In the 'Post a certificate' section click on the 'Browse...' button to
  select a .cer, .crt, .cert, or .pem file.
* Check the top of the window to make sure there are no errors listed, and
  that the desired certificate has been found.
* The data in the text box in the 'Post a certificate' section is the PEM.
* Copy and paste the entire PEM blob, which starts with "-----BEGIN
  CERTIFICATE-----" and ends with "-----END CERTIFICATE-----", into the CCADB.

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
<td> The Common CCADB Policy, says “If an intermediate certificate is revoked, the CCADB must be updated to mark it as revoked, giving the reason why, within 24 hours for a security incident, and within 7 days for any other reason.” 
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
<td> Only fill in this field when this certificate does not contain a CRL URL. Note that the BRs now require intermediate certificates to contain CRL URLs.
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
information for publicly-disclosed and audited intermediate certificates
should be provided on the subordinate CA's website, or the CA's website.
However, if for some reason this is not possible, you can use Mozilla's
Bugzilla bug-tracking system to store the documents and get a URL for use in
the CCADB as follows:

1. If you don't already have a Bugzilla account, [create one][BZ-Create-Acct]
   for yourself.
2. [Search][BZ-Doc-Bugs] to see if there is already a Bugzilla Bug for your CA
   that you can attach your documents to.
3. If one does not exist for your CA, [create one][BZ-Create-Bug].
   * Enter Summary as: "Documents for &lt;your CA's name&gt; intermediate
     certificates"
   * Enter Description as: "The purpose of this bug is to store documents
     related to the publicly disclosed and audited intermediate certificates
     chaining up to &lt;your CA's name&gt; root certificates."
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
[Certsplainer]:   https://tls-observatory.services.mozilla.com/static/certsplainer.html
[BZ-Create-Acct]: https://bugzilla.mozilla.org/createaccount.cgi
[BZ-Doc-Bugs]:    https://bugzilla.mozilla.org/buglist.cgi?&query_format=advanced&component=CA%20Certificate%20Root%20Program&product=NSS&status_whiteboard_type=allwordssubstr&status_whiteboard=ca-audit
[BZ-Create-Bug]:  https://bugzilla.mozilla.org/enter_bug.cgi?&component=CA%20Certificate%20Root%20Program&product=NSS&bug_severity=enhancement
