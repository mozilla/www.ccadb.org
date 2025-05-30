# Information for Auditors # 

The purpose of this page is to assist auditors in communicating with CA Owners during the creation of audit statements that will be submitted for processing by the Audit Letter Validation (ALV) module in the Common CA Database (CCADB).

Audit information for CA Owners can be found [here](https://www.ccadb.org/policy#51-audit-statement-content).

## 1\. Acquire CSV reports of CA Certificates

ALV requires all in-scope SHA-256 fingerprints be included in each of the applicable audit statements. 

A Standard Audit must enumerate all trusted Certification Authority (CA) certificates included in the CA Owner’s CCADB CA hierarchy. A Transport Layer Security (TLS) Baseline Requirements (BR) Audit must enumerate all trusted CA certificates in the CA Owner’s CCADB CA hierarchy that are technically capable of issuing a TLS server authentication certificate. The same is true for certificates issued in accordance with the Extended Validation (EV) Guidelines, Code Signing Baseline Requirements, and S/MIME Baseline Requirements. More detail is included in Section 2 below. 

To identify all of an applicable CA Owner’s SHA-256 fingerprints that should be included in a specific audit statement, it is recommended that Auditor’s download a copy of the “All Certificate Information (root and intermediate) in CCADB ([CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificateRecordsCSVFormatv2))” file from [ccadb.org/resources](http://ccadb.org/resources) and apply a filter for the “CA Owner” and “\[TLS/TLS EVG/S-MIME/Code Signing\] Capable” columns. For example, if you want to identify all fingerprints that should be included in a TLS BR Audit , you can filter first by the “CA Owner” column and then by the “TLS Capable” column where the value is “TRUE”.

## 2\. Create a Preliminary Audit Statement

### Derived Trust Bits indicate whether the CA is “capable of issuing”

While the CCADB requires one Standard Audit and its associated audit statement containing all CA certificates, Root Store Operators also require separate, additional audit statements for all intermediate certificates “capable of issuing” the different types of end entity certificates (e.g., TLS, TLS EV, Code Signing, and S/MIME). Note that CA certificates created by cross-signing are also considered intermediate certificates by Root Stores and must be listed in the CCADB, and they need to be included in all relevant audit statements of the entity that possesses the private key that performed the cross-signing. It is also important to note that audit lists are for CA certificates “capable of issuing” a certain type of end entity certificate. It is irrelevant that the CA Owner tells its auditor that an intermediate CA never has, or never will, issue a certain type of certificate if it is *technically capable* of issuing that type of certificate. For example, if the CCADB indicates that the CA Owner’s “Code Signing Issuing CA” has a “[derived trust bit](https://www.ccadb.org/cas/fields\#formula-fields)” field that indicates the CA is capable of issuing TLS certificates, then the SHA-256 certificate fingerprint for that CA certificate must be included in the TLS Baseline Requirements audit statement. CSV reports generated in accordance with the instructions above should result in a satisfactory list of those CA certificates “capable of issuing” the type of certificate selected. (In the past, CA-provided lists have often failed to include a CA certificate. This will cause the CA certificate to be listed in the CA’s CCADB Task List under “Intermediate Certificates with Outdated Audit Statements” or “Intermediate Certificates with Failed ALV Results”. If not remediated with an updated audit statement, then that CA certificate may have to be revoked, or it may be distrusted by one or more of the Root Store Operators and their respective program.)

### Network and Certificate System Security

Audit statements for compliance with the TLS Baseline Requirements, Code Signing Baseline Requirements, and S/MIME Baseline Requirements must include a statement that the auditor also examined the CA for compliance with the Network and Certificate System Security Requirements (NCSSRs). The NCSSRs are incorporated by reference in each of those previously mentioned standards. Alternatively, the auditor may produce a separate audit statement for the NCSSRs that lists all publicly trusted CA certificates. WebTrust practitioners should use [WebTrust Principles and Criteria for Certification Authorities – Network Security – Version 1.0](https://www.cpacanada.ca/-/media/site/operational/ms-member-services/docs/webtrust/01618\_ms\_network-security.pdf?rev=64c3f42a2a994398925832913e58c55d\&hash=C8F6D0ECA9D05EF4FB589A1AD515FB6A), or newer.  

### Contents and Format of the Audit Statement

Generally, required audit contents are listed here: [https://www.ccadb.org/policy\#51-audit-statement-content](https://www.ccadb.org/policy\#51-audit-statement-content)   
The list of CAs should include the name of the CA, and it must include each of the SHA-256 certificate fingerprints. SHA-256 certificate fingerprints must not contain spaces, colons, or line feeds. While the ALV module can process line wrapping inside the cell of a table, best practice is to include the SHA-256 certificate fingerprint in a single line, e.g.

15DC43B3BDA29DF4546008A4FC306DE811F3E78D804E1B989C2DE11D5336DA1A

Optionally, a smaller font may be used if desired to get everything in one line. Additional details are provided here: [https://www.ccadb.org/policy\#513-alv-formatting](https://www.ccadb.org/policy\#513-alv-formatting) 

## 3\. Save the Preliminary Audit Statement for Review by ALV

Here are [instructions](https://docs.google.com/document/d/12U4az-hjYDC_aWsVn8-Y5vVmJ10inVziAxrQoxP-hfI/edit?usp=sharing) for how to upload a preliminary audit statement for testing with ALV.

CA Owners have the ability to open an “Add/Update Root Request” Case in the CCADB. Instructions for opening this type of Case are found at [https://www.ccadb.org/cas/updates](https://www.ccadb.org/cas/updates). 

The preferred location for saving a preliminary audit statement is a publicly available TLS-secured site hosted either by the CA or the audit firm. During testing, the CA Owner will likely encounter an error message, “Audit Location: Fail (Audit letter not found in certified location)”. The CA Owner can ignore this message during testing. However, if the preliminary audit statement is hosted from the audit firm’s site, then the error “Audit Location: Fail (Audit letter not found in certified location)” may be avoided. The preliminary audit statement should be removed from its temporary location as soon as testing has completed.

## Additional Considerations

### Audit Team Qualifications

[Audit Team Qualifications](https://www.ccadb.org/policy\#52-audit-firm-and-audit-team-qualifications) may be included in the audit statement or provided to the CCADB as a separate attachment.  

On at least an annual basis, the CCADB will check to see whether the audit firm remains accredited. For WebTrust, this is done by checking [https://www.cpacanada.ca/en/business-and-accounting-resources/audit-and-assurance/overview-of-webtrust-services/licensed-webtrust-practitioners-international](https://www.cpacanada.ca/en/business-and-accounting-resources/audit-and-assurance/overview-of-webtrust-services/licensed-webtrust-practitioners-international). 

ETSI auditors (Conformity Assessment Bodies) are responsible for providing the CCADB with a URL where current accreditation can be verified. Members of the ACAB’c should also provide that URL for inclusion on the webpage [https://www.acab-c.com/members/](https://www.acab-c.com/members/).  
