# Automated Data Import

CAs who have a **large** number of intermediate certificates to add to the [CCADB](http://ccadb.org/cas/intermediates) may request that their data be mass imported from a spreadsheet or CSV file, by sending email to their root store operator. Doing the mass import process involves a significant amount of manual work, so if you have less than 20 intermediate certificates please enter them by hand.

## Data Import Process

Intermediate certificate data may be automatically imported from a CSV file for one CA at a time. The data will first be imported into a test environment and checked, before it will be imported into production.

Within the CCADB we will load the CA's data from CSV file(s) into a staging object, which we've called "Migrate Certs". After the data is loaded into the staging object, we can view a staging record for each intermediate cert to be imported, and also view reports on that data. After checking the staging records, we will run a batch program that will read all records from the Migrate Certs object and process them in two steps. Step one prepares a list of qualifying records for processing/reprocessing. Qualifying records are those that have not yet been migrated, and there is already a CCADB record for the Issuing certificate (parent). Step two parses the PEM data of each item from the list and adds the corresponding intermediate certificate record. The batch program may be run multiple times to add child certs or after making data corrections.

When the batch program is no longer updating records, a report of the imported certs will be generated which indicates if the cert was imported or not, and the error if the cert was not imported. The report contains: Certificate Name, Parent Certificate Name, Processing Message/Error, X.509 Certificate (PEM).

For each of the errors, the CA will be responsible for entering the [intermediate certificate data](http://ccadb.org/cas/intermediates) themselves
## Data Import Format

File Format: CSV or Excel Worksheet

## Required Columns
<table width="806px">

<tr>
<th> Column/Field Name </th>
<th> Valid Values </th>
<th> Rules/Notes
</th></tr>
<tr>
<td> PEM </td>
<td>  "-----BEGIN CERTIFICATE----- <br /> &lt;cert PEM data&gt; <br /> -----END CERTIFICATE-----" </td>
<td> Cert PEM data must be enclosed in begin and end tags, and double quotes.
</td></tr>
<tr>
<td> CA Owner/Certificate Name </td>
<td> Certificate Subject Common Name </td>
<td> Max 80 characters allowed. <br />  If the certificate does not have a Subject CN, then use the certificate Subject Organization. <br />  Note: A few additional characters may be added at the end of the name, for clarification purposes, but must be kept consistent within the hierarchy.
</td></tr>
<tr>
<td> Parent CA Owner/Certificate </td>
<td> Certificate Issuer Common Name or Issuer Field </td>
<td> Max 80 characters allowed.
</td></tr>
<tr>
<td> Parent Certificate's SHA-256 Fingerprint </td>
<td> Issuer Cert's SHA-256 Fingerprint </td>
<td> Required. Use this format: 74:F8:A3:C3:EF:E7:B3:90:06:4B:83:90:3C:21:64:60:20:E5:DF:CE
</td></tr>
</table>


## Optional Columns
<table width="806px">
<tr>
<th> Column/Field Name </th>
<th> Valid Values </th>
<th> Rules/Notes
</th></tr>
<tr>
<td> Revocation Status </td>
<td> &lt;blank&gt; <br /> Revoked </td>
<td> Leave blank if not revoked. If this column and the other revocation-related columns are missing, then it will be assumed that the certs are not revoked.
</td></tr>
<tr>
<td> Date of Revocation </td>
<td> &lt;blank&gt; <br /> MM/DD/YYYY </td>
<td> Leave blank if not revoked
</td></tr>
<tr>
<td> <a class="external mw-magiclink-rfc" rel="nofollow" href="//tools.ietf.org/html/rfc5280">RFC 5280</a> Revocation Reason Code </td>
<td> &lt;blank&gt; <br /> (0) unspecified <br /> (1) keyCompromise <br /> (2) cACompromise <br /> (3) affiliationChanged <br /> (4) superseded <br /> (5) cessationOfOperation <br /> (6) certificateHold <br /> (8) removeFromCRL <br /> (9) privilegeWithdrawn <br /> (10) aACompromise </td>
<td> Leave blank if not revoked
</td></tr>
<tr>
<td> Audits Same as Parent </td>
<td> TRUE <br /> FALSE </td>
<td> TRUE if this certificate has the same audit information as the issuing certificate (or a subset). If TRUE, then leave the other audit-related columns empty. If this column and the other audit-related columns are missing, then it will be assumed that this value is TRUE.
</td></tr>
<tr>
<td> Standard Audit </td>
<td> &lt;blank&gt; <br /> URL to audit statement </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE. <br /> Max 255 characters allowed
</td></tr>
<tr>
<td> Standard Audit Type </td>
<td> &lt;blank&gt; <br /> WebTrust <br /> ETSI TS 102 042 <br /> ETSI TS 101 456 </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE
</td></tr>
<tr>
<td> Standard Audit Statement Date </td>
<td> &lt;blank&gt; <br /> MM/DD/YYYY </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE. Date that the audit statement was signed.
</td></tr>
<tr>
<td> BR Audit </td>
<td> &lt;blank&gt; <br /> URL to BR audit statement  </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE, or if Websites Trust Bit not enabled for the root, or cert not capable of issuing SSL/TLS certs.
</td></tr>
<tr>
<td> BR Audit Type </td>
<td> &lt;blank&gt; <br /> WebTrust <br /> ETSI TS 102 042 </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE
</td></tr>
<tr>
<td> BR Audit Statement Date </td>
<td> &lt;blank&gt; <br /> MM/DD/YYYY </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE. Date that the BR audit statement was signed.
</td></tr>
<tr>
<td> EV Audit </td>
<td> &lt;blank&gt; <br /> URL to EV audit statement </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE, or if Websites Trust Bit not enabled for the root, or if this cert is not capable of issuing EV SSL/TLS certs.
</td></tr>
<tr>
<td> EV Audit Type </td>
<td> &lt;blank&gt; <br /> WebTrust <br /> ETSI TS 102 042 </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE
</td></tr>
<tr>
<td> EV Audit Statement Date </td>
<td> &lt;blank&gt; <br /> MM/DD/YYYY </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE. Date that the EV audit statement was signed.
</td></tr>
<tr>
<td> Auditor </td>
<td> &lt;blank&gt; <br /> Auditor's name  </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE. Max 100 characters allowed
</td></tr>
<tr>
<td> Auditor Website </td>
<td> &lt;blank&gt; <br /> URL to the auditor's website, or a site showing their affiliation, accreditation, or qualifications  </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE. Max 300 characters allowed
</td></tr>
<tr>
<td> Auditor Qualifications </td>
<td> &lt;blank&gt; <br /> URL to an attestation of the auditor's qualifications </td>
<td> Leave blank if 'Audits Same as Parent' is TRUE. Max 255 characters allowed
</td></tr>
<tr>
<td> CP/CPS Same as Parent </td>
<td> TRUE <br /> FALSE </td>
<td> TRUE if this certificate has the same policy documentation as the issuing certificate (or a subset). If TRUE, then leave the other policy-related columns empty. If this column and the other CP/CPS columns are missing, then it will be assumed that this value is TRUE.
</td></tr>
<tr>
<td> Policy Documentation </td>
<td> &lt;blank&gt; <br /> Notes about the documentation, such as which language the documents are in, or additional documents that need to be listed.  </td>
<td> Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 1000 characters allowed
</td></tr>
<tr>
<td> CA Document Repository </td>
<td> &lt;blank&gt; <br /> URL to the document repository pertaining to this certificate.  </td>
<td> Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 255 characters allowed
</td></tr>
<tr>
<td> Certificate Policy (CP) </td>
<td> &lt;blank&gt; <br /> URL to the Certificate Policy (CP) pertaining to this certificate.  </td>
<td> Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 300 characters allowed
</td></tr>
<tr>
<td> Certification Practice Statement (CPS) </td>
<td> &lt;blank&gt; <br /> URL to the Certificate Practice Statement (CPS) pertaining to this certificate.  </td>
<td> Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 300 characters allowed
</td></tr>
<tr>
<td> Public Comments </td>
<td> &lt;blank&gt; <br /> Any necessary additional information about the cert, audits, or CP/CPS </td>
<td> Max 2000 characters allowed
</td></tr>
</table>
