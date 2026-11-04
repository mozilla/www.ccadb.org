# Information for Auditors

The purpose of this page is to assist auditors in communicating with CA Owners during the preparation of audit statements that will be submitted for processing by the Audit Letter Validation (ALV) module in the Common CA Database (CCADB).

Audit requirements for CA Owners are specified in [Section 5 of the CCADB Policy](policy#5-audit-disclosures) (see [Section 5.2](policy#52-audit-statement-content) for required audit statement content).

## 1. Acquire CSV Reports of CA Certificates

ALV requires all in-scope SHA-256 fingerprints to be explicitly listed in each applicable audit statement.

A **Standard Audit** must enumerate all trusted Certification Authority (CA) certificates included in the CA Owner's CCADB CA hierarchy. A **Transport Layer Security (TLS) Baseline Requirements (BR) Audit** must enumerate all trusted CA certificates in the CA Owner's CCADB CA hierarchy that are technically capable of issuing a TLS server authentication certificate. The same principle applies to certificates issued in accordance with the **Extended Validation (EV) Guidelines**, **Code Signing Baseline Requirements**, **S/MIME Baseline Requirements**, and **Verified Mark Certificate (VMC) Requirements**. More detail is included in Section 2 below.

To identify all of an applicable CA Owner's SHA-256 fingerprints that should be included in a specific audit statement, auditors should download a copy of the "V5 All Certificate Information (root and intermediate) in the CCADB ([CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificateRecordsCSVFormatV5))" report from [ccadb.org/resources](resources#additional-reports) and filter by the `CA Owner` and `[TLS / TLS EVG / S/MIME / Code Signing] Capable` columns. For example, to identify all fingerprints that should be included in a TLS BR Audit, filter first by the `CA Owner` column and then by the `TLS Capable` column where the value is `TRUE`.

## 2. Create a Preliminary Audit Statement

### Derived Trust Bits Indicate Whether a CA Is "Capable of Issuing"

While the CCADB requires one Standard Audit and its associated audit statement containing all CA certificates, Root Store Operators also require separate, additional audit statements (or clearly scoped criteria within combined reports) for all intermediate certificates "capable of issuing" the different types of end-entity certificates (e.g., TLS, TLS EV, Code Signing, and S/MIME). Note that CA certificates created by cross-signing are also considered intermediate certificates by Root Store Operators, must be disclosed in the CCADB, and must be included in all relevant audit statements of the entity that possesses the private key that performed the cross-signing ([CCADB Policy Section 5.1](policy#51-scope-of-certificates-covered-by-an-audit)).

Audit scope is determined by whether a CA certificate is *technically capable* of issuing a given type of end-entity certificate; it is irrelevant if a CA Owner states that an intermediate CA never has issued, or never will issue, that type of certificate. For example, if the CCADB indicates that a CA Owner's "Code Signing Issuing CA" has `Server Authentication` in its [Derived Trust Bits](cas/fields#system-generated-fields) field, then the SHA-256 certificate fingerprint for that CA certificate must be included in the TLS Baseline Requirements audit statement. Filtering the CSV report generated in accordance with Section 1 above produces the expected list of CA certificates "capable of issuing" each selected certificate type. (Historically, manually compiled lists have often omitted in-scope CA certificates, causing those certificates to appear on the CA Owner's CCADB Task List under `Intermediate Certificates with Outdated Audit Statements` or `Intermediate Certificates with Failed ALV Results`. If not remediated with an updated audit statement, the affected CA certificate may need to be revoked or may be distrusted by one or more Root Store Operators.)

### Network and Certificate System Security

Audit statements for compliance with the TLS Baseline Requirements, Code Signing Baseline Requirements, and S/MIME Baseline Requirements must confirm that the auditor also examined the CA for compliance with the Network and Certificate System Security Requirements (NCSSRs), which are incorporated by reference into those standards. Alternatively, the auditor may produce a separate audit statement for the NCSSRs that lists all publicly trusted CA certificates. WebTrust practitioners should use [WebTrust Principles and Criteria for Certification Authorities - Network Security](https://www.cpacanada.ca/-/media/site/operational/ms-member-services/docs/webtrust/01618_ms_network-security.pdf?rev=64c3f42a2a994398925832913e58c55d&hash=C8F6D0ECA9D05EF4FB589A1AD515FB6A) (Version 1.0 or newer).

### Contents and Format of the Audit Statement

Required audit statement contents are specified in [CCADB Policy Section 5.2 (Audit Statement Content)](policy#52-audit-statement-content).

The list of in-scope CAs should include the name of each CA and **must** include each certificate's uppercase SHA-256 fingerprint encoded as searchable text without spaces, colons, or line feeds. While the ALV module can sometimes process line wrapping inside a table cell, best practice is to render each 64-character SHA-256 certificate fingerprint on a single unbroken line (using a smaller font size if needed), for example:

`15DC43B3BDA29DF4546008A4FC306DE811F3E78D804E1B989C2DE11D5336DA1A`

Full fingerprint and date formatting specifications are provided in [CCADB Policy Section 5.2.3 (ALV Formatting)](policy#523-alv-formatting).

## 3. Save the Preliminary Audit Statement for Review by ALV

Step-by-step instructions for testing preliminary audit statements with ALV before final sign-off are available at [Testing Audit Statements with ALV](cas/ALV#testing-audit-statements-with-alv).

CA Owners can test preliminary audit statements inside an **Add/Update Root Request** case in the CCADB (see [Managing CA Owner and Root Certificate Records](cas/updates#audits)).

The preferred location for hosting a preliminary audit statement is a publicly accessible TLS-secured (`https://`) URL hosted by the audit firm, the CA Owner, or a [Mozilla Bugzilla `CA Documents` attachment](cas/fields#uploading-documents). During preliminary testing from a non-auditor location, the CA Owner will typically see the ALV message `Audit Letter Not Found In Certified Location`, which can be ignored during testing (hosting the preliminary file directly on the audit firm's recognized domain avoids this message). Any preliminary audit statement hosted at a public test URL should be removed once testing is complete and final audit statements are published.

## Additional Considerations

### Audit Team Qualifications

[Audit Team Qualifications](policy#531-audit-team-qualifications) must accompany every audit engagement ([CCADB Policy Section 5.3](policy#53-audit-firm-and-audit-team-qualifications)) and may either be embedded directly within the audit statement PDF or uploaded to the CCADB as a separate text-searchable PDF file.

On at least an annual basis, Root Store Operators verify that each audit firm remains accredited:
* **WebTrust:** Verified against [CPA Canada's Licensed WebTrust Practitioners directory](https://www.cpacanada.ca/en/business-and-accounting-resources/audit-and-assurance/overview-of-webtrust-services/licensed-webtrust-practitioners-international).
* **ETSI:** Conformity Assessment Bodies (CABs) are responsible for providing the CCADB with an authoritative URL where current accreditation can be verified. Members of ACAB'c should also ensure that URL is listed on the [ACAB'c CAB-Member List](https://www.acab-c.com/members/).
