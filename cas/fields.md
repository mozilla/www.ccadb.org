# Field Types and Valid Values #

This document explains how the various records and sections in the CCADB are
best filled out, with some advice on how to create or obtain the data.

## Auditor Information ##

<table border="1">
<tr valign="top"><th>Field Name</th><th>What to Enter</th></tr>

<tr valign="top">
<td>Auditor </td>
<td> Find all Auditors known to the CCADB by clicking on the 'Auditors' report
in the 'Custom Links' section in any Root Certificate, Intermediate Certiifcate, 
or Case page. Contact your root store operator if your auditor is not in this list. 
<br>
To fill in the auditor's name, click on the Edit button, then on the 
search icon (magnifying glass) next to the 'Auditor' field. Then enter the 
first letter of the auditor's name and an asterisk (e.g. B*), then click on 
the 'Go!' button. 
</td>
</tr>
<tr valign="top">
<td>Auditor Location </td>
<td> Find all Auditor Locations known to the CCADB by clicking on the 'Auditors' report
in the 'Custom Links' section in any Root Certificate, Intermediate Certiifcate, 
or Case page. Contact your root store operator if your auditor's location is not in this list. 
<br>
To fill in the auditor's location, click on the Edit button, and first fill in the Auditor.
Then click on the search icon (magnifying glass) next to the 'Auditor Location' field, enter the 
first letter of the auditor's location and an asterisk (e.g. S*), then click on 
the 'Go!' button. </td>
</tr>
</table>

<br>
Auditor qualifications are verified and entered into the CCADB by a root store operator. 
For example, Mozilla re-verifies auditor qualifications annually as described
 [here][Auditor-Qualifications].


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
<td> Choose of the provided options that most closely aligns with the type of audit;
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

## PEM Data ##

The CCADB accepts certificate information in the [PEM][PEM] format. PEM is a
container format defined in RFCs [1421][RFC-1421] to [1424][RFC-1424]. PEM
actually means Privacy Enhanced Mail, but the container format it uses is a
Base64 translation of [X.509][X509] [ASN.1][ASN1] keys.

[Mozilla's TLS Observatory Certificate Explainer][Certsplainer] may be used to
convert a certificate in any other format into PEM, as follows:

* Visit the [Certificate Explainer][Certsplainer].
* In the 'Post a certificate' section click on the 'Browse...' button to
  select a .cer, .crt, .cert, or .pem file.
* Check the top of the window to make sure there are no errors listed, and
  that the desired certificate has been found.
* The data in the text box in the 'Post a certificate' section is the PEM.
* Copy and paste the entire PEM blob, which starts with "-----BEGIN
  CERTIFICATE-----" and ends with "-----END CERTIFICATE-----", into the CCADB.

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
