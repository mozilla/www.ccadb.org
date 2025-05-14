# CCADB Policy

*Version 2.0, Effective: June 15, 2025*

## Introduction

Several Public Root Store Operators have collaborated to create the Common Certification Authority Database (CCADB), a data repository of certificate and Certification Authority (CA) information. 

CA Owners who wish to be included in a CCADB-participating Root Store ("Root Store") need to disclose and maintain certain information in the CCADB. This policy describes common Root Store Operator requirements related to CA Owner use of the CCADB. This policy does not cover how to obtain write access to the CCADB or how to use the CCADB’s web interface. Additional information covering these topics is available [here](https://www.ccadb.org/cas/).

Root Store Operators MAY have additional CCADB-related requirements defined in their own Root Store policies. Those policies MAY strengthen the requirements described in this policy. Additional information on the policies belonging to the individual Root Store Operators participating in the CCADB can be found [here](https://www.ccadb.org/resources). Questions related to an individual Root Store Operator Policy SHOULD be directed to the operator of that policy using the contact address designated for that policy.

## Change History

|Version|Effective Date|
|-|-|
|2.0 (current)|June 15, 2025|
|[1.3.1](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_3_1.md)|October 29, 2024|
|[1.3](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_3.md)|October 25, 2023|
|[1.2.3](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_2_3.md)|July 19, 2023|
|[1.2.2](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_2_2.md)|May 11, 2023|
|[1.2.1](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_2_1.md)|February 17, 2023|
|[1.2](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_2.md)|February 15, 2023|
|[1.1](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_1.md)|December 6, 2021|
|[1.0.5](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_0_5.md)|September 17, 2018|
|[1.0.4](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_0_4.md)|July 16, 2018|
|[1.0.3](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_0_3.md)|May 3, 2018|
|[1.0.2](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_0_2.md)|May 3, 2018|
|[1.0.1](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_0_1.md)|May 3, 2018|
|[1.0](https://github.com/mozilla/www.ccadb.org/blob/master/policy_archive/version_1_0.md)|May 23, 2017|

<br>

## Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this policy are to be interpreted as described in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

This policy considers a "CA Owner" to be the organization or legal entity that is either:

- represented in the subject DN of the CA certificate; or
- in possession or control of the corresponding private key capable of issuing new certificates, if not the same organization or legal entity directly represented in the subject DN of the certificate.

## Table of Contents

1. [General Provisions](policy#1-general-provisions) <br>
2. [Contact Information Disclosures](policy#2-contact-information-disclosures) <br>
3. [Certificate Disclosures](policy#3-certificate-disclosures) <br>
3.1 [Root CA Certificates](policy#31-root-ca-certificates) <br>
3.2 [Subordinate CA Certificates](policy#32-subordinate-ca-certificates) <br>
4. [Policy Disclosures](policy#4-policy-disclosures) <br>
5. [Audit Disclosures](policy#5-policy-disclosures) <br>
5.1 [Scope of certificates covered by an Audit](policy#51-scope-of-certificates-covered-by-an-audit) <br>
5.2 [Audit Statement Content](policy#52-audit-statement-content) <br>
5.3 [Audit Firm and Audit Team Qualifications](policy#53-audit-firm-and-audit-team-qualifications) <br>
6. [Additional Required Practices](policy#6-additional-required-practices) <br>
6.1 [Disclosing and Responding to Incidents](policy#61-disclosing-and-responding-to-incidents) <br>
6.2 [Certificate Revocation List Disclosures](policy#62-certificate-revocation-list-disclosures) <br>
6.3 [Cross-certification across PKI Hierarchies](policy#63-cross-certification-across-pki-hierarchies) <br>
6.4 [Annual CCADB Self-Assessments](policy#64-annual-ccadb-self-assessments) <br>
7. [Mailshots](policy#7-mailshots) <br>

## 1. General Provisions

When required by a Root Store Operator policy, CA Owners MUST adhere to the current version of this policy. Failure to adhere to this policy MAY result in a Root Store Operator disabling a CA Owner’s root certificates, removing them from the corresponding Root Store, or the application of other technical or policy restrictions.

Regardless of more specific provisions in these requirements, CA Owners have an overarching responsibility to keep the information in the CCADB about themselves, their operations and their certificates accurate, and to make updates in a timely fashion. Minimally, CA Owners with certificates included in a Root Store MUST ensure their information stored in the CCADB is kept up to date as changes occur. When a timeline is not defined for a requirement specified in this policy, updates MUST be submitted to the CCADB within 14 calendar days of an activity being completed.

All CCADB disclosures MUST be made freely available and without additional requirements, including, but not limited to, registration, legal agreements, or restrictions on redistribution of the certificates in whole or in part.

All data in the CCADB may be made public or semi-public in a variety of forms. CA Owners SHOULD NOT place any information in the CCADB which they wish to keep confidential. 

Root Store Operators are not obliged to publish any CCADB information.

All client devices that are used to download Personally Identifiable Information from the CCADB SHOULD employ disk-based encryption.

## 2. Contact Information Disclosures

CA Owners MUST provide the following information for a Primary Point of Contact (POC), and at least one other POC, who MAY be a Primary POC:

* Name
* CA Owner-affiliated email address

CA Owners MAY optionally designate further POCs, supplying an email address for each. CA Owners MUST also supply at least one non-personal contact email alias that is more likely to continue working as personnel change; these are maintained as part of the CA’s organizational entry.

All Primary POCs SHOULD be authorized to speak for and enter into binding commitments on behalf of the CA(s) that they represent. The Primary POC will be issued a [CA Community license](https://www.ccadb.org/cas/request-access#application-for-ccadb-access) and MAY request additional licenses for other Primary POCs. Primary POCs are responsible for keeping CCADB data accurate for their CA(s).

Notification of security and audit-related issues MAY be emailed to all individual POCs, non-personal contact email alias(es), or a combination of these addresses. CA Owners are advised to make sure those addresses reach sufficient people such that they can respond to an issue in an appropriate timeframe.

CA Owners MUST maintain up to date contact details in the CCADB. If POC information needs to be updated, the CA Owner MUST submit an [Add/Update Contacts Case](https://www.ccadb.org/cas/contacts). A CA Owner's non-personal contact email alias(es) MUST be updated with an [Add/Update Root Request Case](https://www.ccadb.org/cas/updates).

## 3. Certificate Disclosures

### 3.1 Root CA Certificates

A root CA certificate is a self-signed certificate issued by the root CA to identify itself and to facilitate verification of certificates issued by its corresponding PKI hierarchy. 

CA Owners MUST maintain correct and current information about their root CA certificates. If root CA certificate information needs to be added or updated, the CA Owner MUST submit an [Add/Update Root Request Case](https://www.ccadb.org/cas/updates).

### 3.2 Subordinate CA Certificates

A subordinate CA certificate is a certificate signed by a root CA or another subordinate CA. The CCADB considers the terms "intermediate" and "subordinate" synonymous. 

CA Owners MUST disclose:
- all subordinate CA certificates capable of validating to a certificate included in a Root Store or associated with a CCADB Root Inclusion Request. Disclosure MUST take place within 7 calendar days of issuance and before the subject CA represented in the certificate begins issuing publicly-trusted certificates.
- revocation of all subordinate CA certificates capable of validating to a certificate included in a Root Store or associated with a CCADB Root Inclusion Request within 7 calendar days of revocation.

Cross-certificates (i.e., where the same subject and public key of an existing CA certificate appears in at least one additional certificate issued by a _different_ CA Owner) are considered subordinate CA certificates by Root Store Operators and MUST be disclosed to the issuing CA Owner’s PKI hierarchy in the CCADB. 

Ultimately, this means the subject CA certificate may appear in two distinct CA Owner PKI hierarchies, but it MUST minimally appear in the issuing CA Owner’s.

For any revoked subordinate CA certificate, each corresponding revocation entry published to a CRL MUST include a reasonCode extension. If the revocation is due to a security concern, the CA Owner MUST file a secure (i.e., "confidential") [Incident Report](https://www.ccadb.org/cas/incident-report#how-do-i-submit-a-security-sensitive-incident-report) in Bugzilla, with the expectation that a public Incident Report will eventually be filed.

## 4. Policy Disclosures

CCADB enables associating PKI policy documents in the records for both root CA certificates and subordinate CA certificates.

CA Owners with either (1) a certificate included in a Root Store or (2) a CA certificate that validates to a certificate included in a Root Store MUST minimally:

- accurately describe the policies and practices of their CA(s) within a Certificate Policy (CP) and corresponding Certification Practice Statement (CPS), or preferably, a single document combined as a CP/CPS.
- ensure the CA policy documents are:
    - freely publicly available for examination.
    - available in an authoritative English language version.
    - sufficiently detailed to assess the operations of the CA(s) and the compliance with the expectations set forth in this Policy, the applicable CA/Browser Forum Baseline Requirements, and any applicable Root Store Operator policies, and MUST NOT conflict with any of the requirements specified therein.

To promote simplicity and clarity, all CA policy documents SHOULD be:
- focused on one specific PKI use case (e.g., TLS server authentication, TLS client authentication, S/MIME, Code Signing, etc.), rather than combining multiple use cases into a single document or set of documents.
- comprehensive and consolidated, whenever possible, such that there are not multiple sets of similar yet slightly different policy and practice statements supporting the same PKI use case.
- available in Markdown or AsciiDoc.

CA Owners MUST strictly adhere to their policy document(s) as disclosed within the CCADB (and not marked as “Superseded”). This extends to all policy documents the CA Owner publishes in relation to its CAs included in a Root Store, such as TSPS documents.

CA Owners MUST ensure that updated versions of a CA's policy document(s) are uploaded to their own publicly accessible repository before the corresponding policy changes are put into practice. Corresponding policy changes are considered to be put into practice on the effective date specified in the policy document(s), unless individual requirements are explicitly future dated.
Separately, CA Owners SHOULD ensure these updated policy document(s) are submitted to the CCADB within 7 calendar days of the policy document's effective date, and MUST ensure they are submitted within 14 calendar days of that effective date.

CA Owners MUST:
- submit an [Add/Update Root Request Case](https://www.ccadb.org/cas/updates) to add or update policy documents for root CA certificates stored in the CCADB.
- add or update  policy documents for subordinate CA certificates directly on the record in CCADB (unless the exceptions stated below apply).

Unless the exceptions below apply, CA policy disclosures for each certificate disclosed to the CCADB MUST be consistent with the following guidance:

If the parent certificate record discloses a CP or CPS:
- A) It MUST disclose both a CP and a CPS
- B) It MUST NOT disclose a CP/CPS
- C) All child certificate records MUST either:
     - (1) disclose a combined CP/CPS; or
     - (2) disclose (a) a CP (either select "Same as Parent" checkbox or a different CP) and (b) a CPS (either select "Same as Parent" checkbox or a different CPS).

If the parent certificate record discloses a combined CP/CPS:
- A) It MUST NOT disclose a CP
- B) It MUST NOT disclose a CPS
- C) All child certificate records MUST either:
     - (1) disclose the same combined CP/CPS (using the "Same as Parent" checkbox);
     - (2) disclose a different CP/CPS; or
     - (3) disclose a CP and a CPS.

Exceptions to providing these policy document URLs:

- The certificate has expired; or
- The certificate has been revoked, and the corresponding record in the CCADB has been updated with the correct revocation status.

## 5. Audit Disclosures

Beyond policy disclosures, CCADB also enables associating statements of attestation of CA Owner conformance to various requirements and other operational criteria ("audits").

The URLs to such audit statements and any metadata about them such as the name of the auditor or the date of the audit MUST be updated as new information becomes available. For technical reasons, URLs to audit statements MUST point to a PDF file that conforms to Audit Letter Validation (ALV) and either WebTrust or Accredited Conformity Assessment Bodies’ Council (ACAB'c) formatting standards.

The entry for each subordinate CA certificate has checkboxes to indicate "Audits Same as Parent". When the checkbox is checked, the details do not need to be duplicated from the parent certificate. However, the subordinate CA certificate MUST be specifically listed in the audit statements of the parent certificate.

URLs for the following audit statements are required for each CA certificate, depending upon the purposes for which the certificate and those it issues are trusted. 

| Trust Purpose | Description | Audits Required |  
|---|---|---|
| Server Authentication  | Any certificate issued by the CA (directly or transitively) contains an EKU value of: <br><br> (1) either 1.3.6.1.5.5.7.3.1 (id-kp-serverAuth) or 1.3.6.1.5.5.7.3.0 (anyExtendedKeyUsage), or <br><br> (2) No EKU | (1) Standard Audit <br><br> (2) NetSec Audit <br><br> (3) TLS BR Audit <br><br> (4) TLS EVG Audit (_only if issuing certificates that contain the CA/Browser Forum EV Certificate Policy Identifier (2.23.140.1.1)_) |
| Client Authentication | Any certificate issued by the CA (directly or transitively) contains an EKU value of: <br><br> (1) either 1.3.6.1.5.5.7.3.2 (id-kp-clientAuth) or 1.3.6.1.5.5.7.3.0 (anyExtendedKeyUsage), or <br><br> (2) No EKU  | (1) Standard Audit <br><br> (2) NetSec Audit <br><br> (3) TLS BR Audit <br><br> (4) TLS EVG Audit (_only if issuing certificates that contain the CA/Browser Forum EV Certificate Policy Identifier (2.23.140.1.1)_) |
| Code Signing           | Any certificate issued by the CA (directly or transitively) contains an EKU value of: <br><br>(1) either 1.3.6.1.5.5.7.3.3 (id-kp-codeSigning) or 1.3.6.1.5.5.7.3.0 (anyExtendedKeyUsage), or <br><br> (2) No EKU    | (1) Standard Audit <br><br> (2) NetSec Audit <br><br> (3) Code Signing Audit   |
| Secure Email           | Any certificate issued by the CA (directly or transitively) contains an EKU value of: <br><br>(1) either 1.3.6.1.5.5.7.3.4 (id-kp-emailProtection) or 1.3.6.1.5.5.7.3.0 (anyExtendedKeyUsage), or <br><br> (2) No EKU   | (1) Standard Audit <br><br> (2) NetSec Audit <br><br> (3) S/MIME BR Audit  |

Some Root Store Operators require additional audit disclosures to the CCADB.

Exceptions to providing these audit statement URLs:

* The SHA-256 fingerprint of the certificate is specifically listed as in scope in the audit statements of the parent certificate, and the "Audits Same as Parent" checkbox is checked; or
* The certificate has expired; or
* The certificate has been revoked, and the corresponding record in the CCADB has been updated with the correct revocation status; or
* The certificate was issued after the audit period of the most recently performed audit. In such cases, the certificate MUST be included in the scope of the CA Owner's next periodic audit.

CA Owners MUST:
- submit an [Add/Update Root Request Case](https://www.ccadb.org/cas/updates) to add or update audit statements for root CA certificates stored in the CCADB.
- add or update audit statements for subordinate CA certificates directly on the record in the CCADB (unless the exceptions stated above apply).

If an audit or audit statement disclosed to the CCADB does not meet the requirements of this policy, then a Root Store Operator MAY require that the CA Owner obtain a new audit, at the CA Owner's expense, for the period of time in question. Additionally, depending on the nature of concerns with the audit, a Root Store Operator MAY require that the CA Owner obtain such an audit from a new auditor.

The presence of qualifications in an audit statement is not, by itself, generally considered a reason to remove a CA Owner from a Root Store. The purpose of audits is to honestly and thoroughly assess a CA Owner’s compliance with requirements which are necessary to assure a secure and stable ecosystem. Audit findings, including qualifications, can help to identify opportunities for improvement, whether for individual CAR Owners or for the wider industry as a whole.

### 5.1 Scope of Certificates Covered by an Audit

CA certificates MUST appear in the Issuer’s annual audit statement, beginning with the statement corresponding to the audit period when the certificate was issued. Those certificates MUST continue to appear in audit statements until having appeared on at least one audit statement following revocation, expiration, or key destruction (observed and reported by a Qualified Auditor).
Self-signed certificates that share a Subject + SPKI with a root certificate that is, or was, included in a Root Store are treated by Root Store Operators as subordinate CA certificates because they chain up to an included root, so these certificates MUST also be listed in the applicable audit statements according to the [Derived Trust Bits](https://www.ccadb.org/cas/fields#formula-fields) field.
CA certificates created by cross-signing are also considered subordinate CA certificates by Root Store Operators and MUST be included in all relevant audit statements of the entity that possesses the private key that performed the cross-signing.

Cross-certificates issued before June 15, 2025 that DO NOT contain an EKU MUST appear in all of the Issuer’s annual audit statements for its corresponding Trust Purposes ([described above](policy#5-policy-disclosures)).

### 5.2 Audit Statement Content

An authoritative English language version of publicly available audit information MUST be uploaded to the CCADB no later than 92 calendar days from the point-in-time date or the end date of the period of time. In the event of a delay greater than 92 calendar days, the CA Owner MUST provide an explanatory letter signed by the Qualified Auditor. The CCADB warns Root Store Operators when the audit periods are not consecutive.

Reports uploaded to the CCADB MUST be publicly available and contain at least the following clearly-labeled text-searchable information: 

1. Full name of the CA Owner or corresponding Affiliate (e.g., organization providing external RA services) that was audited;
2. Name and address of the organization performing the audit;
3. Qualifications of the team performing the audit;
4. The physical locations that were and were not audited;
5. SHA-256 fingerprint of each root and subordinate CA certificate that was in scope of the audit (see format specifications below);
6. Full names and version numbers of the audit standards that were used during the audit;
7. List of the CA Owner's applicable policy documents (with version numbers and publication dates) referenced during the audit;
8. Whether the audit is for a period of time or a point in time;
9. Start date and end date of the period that was audited, for those that cover a period of time (this is not the period the auditor was on-site);
10. Point-in-time date, for those that are for a point in time;
11. Date the audit statement was issued (referred to as the "issuing date" by the ACAB'c Audit Attestation Letter templates and "report date" by the WebTrust Illustrative Reports);
    - For revised or corrected versions of audit statements made to address errors, omissions, or formatting to a previously completed audit statement, the CA Owner may enter the date of the initial issuance, provided that the scope and audit period covered by the revised audit statement remain unchanged. In such cases, the audit statement should contain the initial issuance date and the subsequent issuance date and the CA Owner should provide the URL of the most recent version and include a comment in the case explaining the revision date and the reason for reissuance of the audit statement.
12. For ETSI, a statement to indicate if the audit was a full audit, and which parts of the criteria were applied, e.g. DVCP, OVCP, NCP, NCP+, LCP, EVCP, EVCP+, QCP-w, Part1 (General Requirements), and/or Part 2 (Requirements for trust service providers), and a statement to indicate that the auditor referenced the applicable CA/Browser Forum criteria and the version used;
13. All incidents disclosed by the CA Owner, or reported by a third party, and all findings reported by an auditor, that, at any time during the audit period, occurred, were open in Bugzilla, or were reported to a Root Store Operator; and
14. An explicit statement indicating the audit covers the relevant systems and processes used in the issuance of all certificates that assert one or more of the policy identifiers listed below:

For hierarchies used to issue TLS certificates:
- 2.23.140.1.2.1
- 2.23.140.1.2.2
- 2.23.140.1.2.3
- 2.23.140.1.1

For hierarchies used to issue Code Signing certificates:
- 2.23.140.1.4.1
- 2.23.140.1.4.2
- 2.23.140.1.3

For hierarchies used to issue S/MIME certificates:
- 2.23.140.1.5.1.1
- 2.23.140.1.5.1.2
- 2.23.140.1.5.1.3
- 2.23.140.1.5.2.1
- 2.23.140.1.5.2.2
- 2.23.140.1.5.2.3
- 2.23.140.1.5.3.1
- 2.23.140.1.5.3.2
- 2.23.140.1.5.3.3
- 2.23.140.1.5.4.1
- 2.23.140.1.5.4.2
- 2.23.140.1.5.4.3

#### 5.2.1 ETSI

Audits conducted by an accredited Conformity Assessment Body (CAB) MUST have their Audit Attestation Letter (AAL) uploaded to the CAB’s website. CA Owners provide the URL to the AAL on the CAB’s website, and ALV will verify those URLs against a list of approved CAB websites. ETSI AALs MUST follow the latest version of the AAL template on the ACAB'c [website](https://www.acab-c.com/downloads/).

When the AAL cannot be posted on the CAB's website, the CA Owner MAY post the AAL on their own website or attach the attestation report to a [Bugzilla Bug](https://www.ccadb.org/cas/fields#uploading-documents) and provide that URL. The authenticity of the AAL will still need to be established by the CAB. 

#### 5.2.2 WebTrust

Unqualified WebTrust audit statements provided by licensed WebTrust practitioners MUST have a WebTrust Seal. Qualified WebTrust audit statements provided by licensed WebTrust practitioners SHOULD have a WebTrust Seal. Whether unqualified or qualified, CAs enter the URL of the WebTrust Seal into the CCADB, and upon saving the record, the CCADB automatically converts the URL to point to the corresponding PDF file via integration with CPA Canada.

For qualified WebTrust audits, if a Seal is not obtained from CPA Canada, then the CA Owner MUST post the audit statement on their own website or attach the audit statement to a [Bugzilla Bug](https://www.ccadb.org/cas/fields#uploading-documents) and provide that URL. The authenticity of any WebTrust audit statement not provided with a Seal from CPA Canada will still need to be established with the auditor.

#### 5.2.3 ALV Formatting

The CCADB uses an application called Audit Letter Validation to automatically parse and validate audit statements. This system eliminates manual processing, but it requires audit statements to follow some basic rules in order to function properly. If the audit statement fails to meet any of the following requirements, the CA Owner MUST work with their auditor to provide an audit statement that passes ALV.

Format Specifications for SHA-256 Fingerprints:

* MUST: No colons, no spaces, and no line feeds
* MUST: Uppercase letters
* MUST: Be encoded in the document (PDF) as text searchable, not an image

Format Specifications for Dates: The following formats are accepted by ALV:

* Month DD, YYYY example: May 7, 2016
* DD Month YYYY example: 7 May 2016
* YYYY-MM-DD example: 2016-05-07
* Month names in English
* No extra text within the date, such as "7th" or "the"

ALV supports the following format for specifying audit period date ranges:

<br>
```<date><space><splitter><space><date>```
<br><br>
    
Where splitter MUST be one of the following:
* to
* through
* until
* and
* \-
* \~

### 5.3 Audit Firm and Audit Team Qualifications

CA Owners MUST ensure audits used to comply with this policy are performed by entities licensed or otherwise permitted to provide assurance services in the country(ies) where the assessment is performed, for the entirety of the audit engagement’s duration.

#### 5.3.1 Audit Team Qualifications

Each audit statement MUST be accompanied by documentation of the audit team qualifications sufficient to determine the competence, experience, and independence of the auditor. This documentation MAY be part of the audit statement, or MAY be provided as a separate text-searchable PDF file, and MUST contain the following information:

* Date that the audit report was signed;
* Full name of the CA Owner that was audited;
* Name and address of the audit firm or CAB;
* Audit criteria (e.g., ETSI / WebTrust);
* Proof of audit firm or CAB Accreditation URL (e.g., the auditor is listed in [CPA Canada's Licensed WebTrust practitioners web page](https://www.cpacanada.ca/en/business-and-accounting-resources/audit-and-assurance/overview-of-webtrust-services/licensed-webtrust-practitioners-international) or the CAB’s name and [Accreditation Attestation](https://european-accreditation.org/ea-%20members/directory-of-ea-members-and-mla-signatories/) are listed in the [ACAB'c CAB-member List](https://www.acab-c.com/members/));
* Name of Lead Auditor or Signing Partner (except where prohibited by law or other public policy, in which case, we ask that you not provide any personally identifiable information in the document);
* For the audit team and the audit Quality Reviewer or QA Partner, qualification information such as:
    - Number of audit team members;
    - Academic qualifications or professional training received;
    - Average years of auditing experience auditing trust services or similar information systems;
    - Experience, special skills, and qualifications (e.g., audit/assessment principles and functions, information technology, software development, trust services, public key infrastructure, CA operations, and information security including risk assessment/management, network security, physical security, etc.); and
    - Credentials, designations, or certifications (e.g., CPA, CISA, CITP, CISSP, CCSP/CCA/CCP, etc.).
* How the audit team and team members are bound by law, regulation or professional standards to render an independent assessment of the CA (e.g., https://pub.aicpa.org/codeofconduct/Ethics.aspx# 0.300.050 Objectivity and Independence; CPA Canada, Rule 204; or Annex A of ETSI EN 319 403/403-1, respectively); and
* Whether the audit team relied on any third-party specialists or affiliate audit firms, and if so, their names and where they performed services.

## 6. Additional Required Practices

### 6.1 Disclosing and Responding to Incidents

The CCADB [Incident Reporting Guidelines (IRGs)](https://www.ccadb.org/cas/incident-report) intend to present a common format for publicly disclosing incidents. CA Owners who are required to publicly disclose incidents:
- SHOULD always use the latest available version of the CCADB IRG templates, and
- MUST NOT use a version of an IRG template that has been superseded by more than 30 calendar days before the corresponding report (i.e., preliminary, full, or closure) is posted.

### 6.2 Certificate Revocation List Disclosures

For each unexpired and unrevoked CA certificate record disclosed to the CCADB and within 7 days of the corresponding CA issuing its first certificate, CA Owners MUST disclose either:
- the URL of a full and complete Certificate Revocation List (CRL); or
- a JSON Array of Partitioned CRL URLs.

URLs:
- MUST match exactly as they appear in the certificates issued by the corresponding CA.

If populating a full and complete CRL URL: 
- the corresponding CRL SHOULD NOT contain an 'Issuing Distribution Point' extension.
- the JSON Array of Partitioned CRL URLs field MUST be empty.

If populating a JSON Array of Partitioned CRL URLs: 
- CA Owners MUST ensure that each corresponding CRL contains a critical 'Issuing Distribution Point' extension and the 'distributionPoint' field of the extension MUST include a 'UniformResourceIdentifier'. The value of the UniformResourceIdentifier MUST exactly match a URL, from which the CRL was accessed, present in the CCADB record associated with the CA certificate.
- the full and complete CRL URL MUST be empty.

Under normal operating conditions, the CRL URLs provided by CAs in accordance with this section MUST be available such that relying parties are able to successfully retrieve the current CRL every 4 hours.

### 6.3 Cross-certification across PKI Hierarchies

Some Root Store Operators participating in the CCADB maintain policy requirements such that hierarchies included in the corresponding root store(s) are dedicated to a specific PKI use case, for example only supporting TLS server authentication. 

In support of ubiquity use-cases, CA Owners sometimes issue cross-certificates from non-dedicated hierarchy Root CAs (i.e., “multi-purpose hierarchies”) to dedicated-use hierarchy Root CAs. 

Beginning June 15, 2025, when new cross-certificates are issued across PKI hierarchies and the Subject CA’s public key (a) exists in or (b) might exist in a publicly-trusted self-signed Root CA certificate whose hierarchy should be considered dedicated to a specific PKI use case, the following EKU values MUST exist:

| If the subject hierarchy is dedicated to… | EKU Presence? | EKU OID Permitted? |
|---|---|---|
| TLS server authentication | MUST | Only 1.3.6.1.5.5.7.3.1                       |
| TLS client authentication | MUST | Only 1.3.6.1.5.5.7.3.2                       |
| TLS (generic)             | MUST | Only 1.3.6.1.5.5.7.3.1 and 1.3.6.1.5.5.7.3.2 |
| S/MIME                    | MUST | Only 1.3.6.1.5.5.7.3.4                       |
| S/MIME (generic)             | MUST | Only 1.3.6.1.5.5.7.3.4 and 1.3.6.1.5.5.7.3.2 |
| Code signing              | MUST | Only 1.3.6.1.5.5.7.3.3                       |

In cases where both the Issuer and the Subject hierarchies are capable of issuing Extended Validation (EV) certificates, the cross-certificate MUST include the EV CA/Browser Forum Reserved Certificate Policy Identifier of 2.23.140.1.1 as a policyIdentifier. Additional policyIdentifiers MAY be present.

### 6.4 Annual CCADB Self-Assessments

At least annually, CA Owners MUST complete a self-assessment using [this](https://www.ccadb.org/cas/self-assessment) template to attest to the conformance of the CA Owner’s policies against industry policies and practices. CA Owners SHOULD always use the latest available version of the self-assessment template. CA Owners MUST NOT use a version of the self-assessment template that has been superseded by more than 90 calendar days before their submission.

A single self-assessment MAY cover multiple CAs operating under both the same CP and CPS(s), or combined CP/CPS. CAs not operated under the same CP and CPS(s) or combined CP/CPS MUST be covered in a separate self-assessment.

The self-assessment submission date is determined by the earliest appearing "BR Audit Period End Date" field specified in any of the CA Owner’s "CA Owner/Certificate" CCADB root records that are included in one or more Root Stores. 

An annual self-assessment MUST be completed and submitted to the CCADB within 92 calendar days from the CA Owner's earliest appearing root record "BR Audit Period End Date." CA Owners SHOULD submit the self-assessment to the CCADB at the same time as uploading audit reports.

## 7. Mailshots

From time to time, a Root Store Operator MAY use the CCADB to send information to CA Owners. Mailshots will be sent to at least the Primary POC(s) and the CA Owners' email aliases, and may also go to one or more of the other POCs; the exact recipient list is defined by the Root Store Operator sending the information.

-----

Any copyright in this document is [dedicated to the Public Domain](https://creativecommons.org/publicdomain/zero/1.0/).
