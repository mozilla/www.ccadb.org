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
<table class="wikitable">

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

| Column/Field Name | Valid Values | Rules/Notes |
| --- | --- | --- |
|PEM|"-----BEGIN CERTIFICATE-----  <cert PEM data>  -----END CERTIFICATE-----"|Cert PEM data must be enclosed in begin and end tags, and double quotes.|
|CA Owner/Certificate Name|Certificate Subject Common Name|Max 80 characters allowed.   If the certificate does not have a Subject CN, then use the certificate Subject Organization.   Note: A few additional characters may be added at the end of the name, for clarification purposes, but must be kept consistent within the hierarchy.|
|Parent CA Owner/Certificate|Certificate Issuer Common Name or Issuer Field|Max 80 characters allowed.|
|Parent Certificate's SHA-256 Fingerprint|Issuer Cert's SHA-256 Fingerprint|Required. Use this format: 74:F8:A3:C3:EF:E7:B3:90:06:4B:83:90:3C:21:64:60:20:E5:DF:CE|
  
## Optional Columns
| Column/Field Name | Valid Values | Rules/Notes|
|--- |--- |--- |
|Revocation Status|<blank>  Revoked|Leave blank if not revoked. If this column and the other revocation-related columns are missing, then it will be assumed that the certs are not revoked.|
|Date of Revocation|<blank>  MM/DD/YYYY|Leave blank if not revoked|
|RFC 5280 Revocation Reason Code|<blank>  (0) unspecified  (1) keyCompromise  (2) cACompromise  (3) affiliationChanged  (4) superseded  (5) cessationOfOperation  (6) certificateHold  (8) removeFromCRL  (9) privilegeWithdrawn  (10) aACompromise|Leave blank if not revoked|
|Audits Same as Parent|TRUE  FALSE|TRUE if this certificate has the same audit information as the issuing certificate (or a subset). If TRUE, then leave the other audit-related columns empty. If this column and the other audit-related columns are missing, then it will be assumed that this value is TRUE.|
|Standard Audit|<blank>  URL to audit statement|Leave blank if 'Audits Same as Parent' is TRUE.  Max 255 characters allowed|
|Standard Audit Type|<blank>  WebTrust  ETSI TS 102 042  ETSI TS 101 456|Leave blank if 'Audits Same as Parent' is TRUE|
|Standard Audit Statement Date|<blank>  MM/DD/YYYY|Leave blank if 'Audits Same as Parent' is TRUE. Date that the audit statement was signed.|
|BR Audit|<blank>  URL to BR audit statement|Leave blank if 'Audits Same as Parent' is TRUE, or if Websites Trust Bit not enabled for the root, or cert not capable of issuing SSL/TLS certs.|
|BR Audit Type|<blank>  WebTrust  ETSI TS 102 042|Leave blank if 'Audits Same as Parent' is TRUE|
|BR Audit Statement Date|<blank>  MM/DD/YYYY|Leave blank if 'Audits Same as Parent' is TRUE. Date that the BR audit statement was signed.|
|EV Audit|<blank>  URL to EV audit statement|Leave blank if 'Audits Same as Parent' is TRUE, or if Websites Trust Bit not enabled for the root, or if this cert is not capable of issuing EV SSL/TLS certs.|
|EV Audit Type|<blank>  WebTrust  ETSI TS 102 042|Leave blank if 'Audits Same as Parent' is TRUE|
|EV Audit Statement Date|<blank>  MM/DD/YYYY|Leave blank if 'Audits Same as Parent' is TRUE. Date that the EV audit statement was signed.|
|Auditor|<blank>  Auditor's name|Leave blank if 'Audits Same as Parent' is TRUE. Max 100 characters allowed|
|Auditor Website|<blank>  URL to the auditor's website, or a site showing their affiliation, accreditation, or qualifications|Leave blank if 'Audits Same as Parent' is TRUE. Max 300 characters allowed|
|Auditor Qualifications|<blank>  URL to an attestation of the auditor's qualifications|Leave blank if 'Audits Same as Parent' is TRUE. Max 255 characters allowed|
|CP/CPS Same as Parent|TRUE  FALSE|TRUE if this certificate has the same policy documentation as the issuing certificate (or a subset). If TRUE, then leave the other policy-related columns empty. If this column and the other CP/CPS columns are missing, then it will be assumed that this value is TRUE.|
|Policy Documentation|<blank>  Notes about the documentation, such as which language the documents are in, or additional documents that need to be listed.|Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 1000 characters allowed|
|CA Document Repository|<blank>  URL to the document repository pertaining to this certificate.|Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 255 characters allowed|
|Certificate Policy (CP)|<blank>  URL to the Certificate Policy (CP) pertaining to this certificate.|Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 300 characters allowed|
|Certification Practice Statement (CPS)|<blank>  URL to the Certificate Practice Statement (CPS) pertaining to this certificate.|Leave blank if 'CP/CPS Same as Parent' is TRUE. Max 300 characters allowed|
|Public Comments|<blank>  Any necessary additional information about the cert, audits, or CP/CPS|Max 2000 characters allowed|
