# Field Types and Valid Values #

This document explains how the various records and sections in the CCADB are
best filled out, with some advice on how to create or obtain the data.

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
<tr valign="top">
<td>Standard Audit </td>
<td>URL to an auditor's statement that the operation of this certificate has
been audited according to one of:
<ul>
<li>ETSI TS 101 456 V1.4.3 or later (only applicable to non-SSL certs)</li>
<li>ETSI TS 102 042 V2.3.1 or later</li>
<li>ETSI EN 319 411-1 v1.1.1 or later</li>
<li>ETSI EN 319 411-2 v2.1.1 or later</li>
<li>WebTrust Principles and Criteria for Certification Authorities v2.0 or
later</li>
</ul>
</td>
</tr>
<tr valign="top">
<td>Standard Audit Type </td>
<td> One of:
<ul>
<li>WebTrust</li>
<li>ETSI EN 319 411</li>
<li>ETSI TS 101 456</li>
<li>ETSI TS 102 042</li>
</ul>
</td>
</tr>
<tr valign="top">
<td>Standard Audit Period </td>
<td>For each Audit Statement provide the Audit Period Start Date and Audit
Period End Date. In a period‐of‐time audit, the Audit Period is the period
between the first day (start) and the last day of operations (end) covered by
the auditors in their engagement.

The period during which the CA issues Certificates SHALL be divided into an
unbroken sequence of audit periods. An audit period MUST NOT exceed one year
in duration.
</td>
</tr>
<tr valign="top">
<td>Standard Audit Statement Date </td>
<td> Date that the audit statement was signed.</td>
</tr>
<tr valign="top">
<td>BR Audit </td>
<td> URL to a corresponding Baseline Requirements audit statement. Only
required if the root certificate has the Websites trust bit enabled, and this
certificate is capable of issuing SSL/TLS certificates. </td>
</tr>
<tr valign="top">
<td>BR Audit Type </td>
<td> One of:
<ul>
<li>WebTrust</li>
<li>ETSI EN 319 411</li>
<li>ETSI TS 102 042</li>
</ul>
</td>
</tr>
<tr valign="top">
<td>BR Audit Statement Date </td>
<td> Date that the BR audit statement was signed.</td>
</tr>
<tr valign="top">
<td>EV Audit </td>
<td> URL to a corresponding EV audit statement. Only required if the root
certificate has EV-treatment, and this certificate is capable of issuing EV
SSL/TLS certificates.</td>
</tr>
<tr valign="top">
<td>EV Audit Type </td>
<td> One of:
<ul>
<li>WebTrust</li>
<li>ETSI EN 319 411</li>
<li>ETSI TS 102 042</li>
</ul>
</td>
</tr>
<tr valign="top">
<td>EV Audit Statement Date </td>
<td> Date that the EV audit statement was signed.</td>
</tr>
<tr valign="top">
<td>Auditor </td>
<td> The Auditor's name</td>
</tr>
<tr valign="top">
<td>Auditor Website </td>
<td> URL to the auditor's website, or a site showing their affiliation,
accreditation, or qualifications</td>
</tr>
<tr valign="top">
<td>Auditor Qualifications </td>
<td> URL to an attestation of the auditor's qualifications.
</td>
</tr>
<tr valign="top">
<td>Management Assertions By </td>
<td> The name (in English) of the organization who made the management
assertions for the Standard Audit. i.e. The name of the organization that
validates the data to be included in certificates signed by this issuer.</td>
</tr>
</table>

<br>
If you need help finding a suitable URL to demonstrate the qualifications of
your auditor, try [this list][WT-Auditors] for WebTrust, or see one of
[these][ETSI-Auditors1] [three][ETSI-Auditors2] [sites][ETSI-Auditors3] for
ETSI.

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

[WT-Auditors]:    http://www.webtrust.org/licensed-webtrust-practitioners-international/item64419.aspx
[ETSI-Auditors1]: http://www.dakks.de/en/content/accredited-bodies-dakks
[ETSI-Auditors2]: https://www.acab-c.com/accredited-bodies/
[ETSI-Auditors3]: https://www.ukas.com/
[PEM]:            https://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions
[RFC-1421]:       https://tools.ietf.org/html/rfc1421
[RFC-1424]:       https://tools.ietf.org/html/rfc1424
[X509]:           https://en.wikipedia.org/wiki/X.509
[ASN1]:           https://en.wikipedia.org/wiki/Abstract_Syntax_Notation_One
[Certsplainer]:   https://tls-observatory.services.mozilla.com/static/certsplainer.html
[BZ-Create-Acct]: https://bugzilla.mozilla.org/createaccount.cgi
[BZ-Doc-Bugs]:    https://bugzilla.mozilla.org/buglist.cgi?&query_format=advanced&component=CA%20Certificate%20Root%20Program&product=NSS&status_whiteboard_type=allwordssubstr&status_whiteboard=ca-audit
[BZ-Create-Bug]:  https://bugzilla.mozilla.org/enter_bug.cgi?&component=CA%20Certificate%20Root%20Program&product=NSS&bug_severity=enhancement
