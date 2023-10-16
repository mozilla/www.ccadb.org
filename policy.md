# CCADB Policy #

*Version 1.3.0, Effective: October 25, 2023*

## Introduction
Several Web PKI root store operators (“Stores”) have collaborated to create the Common Certification Authority Database (CCADB), a data repository of certificate and Certification Authority (CA) information. CA Owners who wish to be included in participating Stores will need to maintain certain information in the CCADB. This document explains what is required of CA Owners who are required by Store policy to use the CCADB.

Stores may have their own additional CCADB-related requirements. For each root certificate, CA Owners must comply with the additional requirements pertaining to the Stores which contain that certificate. Additional information on Store requirements can be found [here](https://www.ccadb.org/resources).

This policy does not cover how to obtain write access to the CCADB or how to use the CCADB’s web interface. Additional information covering these topics is available [here](https://www.ccadb.org/cas/).

## Change History

|Version|Effective Date|
|-|-|
|[1.0](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_0.md)|May 23, 2017|
|[1.0.1](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_0_1.md)|May 3, 2018|
|[1.0.2](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_0_2.md)|May 3, 2018|
|[1.0.3](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_0_3.md)|May 3, 2018|
|[1.0.4](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_0_4.md)|July 16, 2018|
|[1.0.5](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_0_5.md)|September 17, 2018|
|[1.1](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_1.md)|December 6, 2021|
|[1.2](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_2.md)|February 15, 2023|
|[1.2.1](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_2_1.md)|February 17, 2023|
|[1.2.2](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_2_2.md)|May 11, 2023|
|[1.2.3](https://github.com/mozilla/www.ccadb.org/blob/add-policy-history/policy_archive/version_1_2_3.md)|July 19, 2023|
|1.3 (current)|October 25, 2023|

<br>

## Table of Contents
1. [General Provisions](policy#1-general-provisions)
2. [Contact Information](policy#2-contact-information)
3. [Root CA Certificates](policy#3-root-ca-certificates)
4. [Subordinate CA Certificates](policy#4-subordinate-ca-certificates)
5. [Policies, Audits, and Audit Practices](policy#5-policies-audits-and-practices) <br>
5.1 [Audit Statement Content](policy#51-audit-statement-content) <br>
5.2 [Audit Firm and Audit Team Qualifications](policy#52-audit-firm-and-audit-team-qualifications) <br>
5.3 [Annual CCADB Self-Assessments](policy#53-annual-ccadb-self-assessments) <br>
6. [Mailshots](policy#6-mailshots)


## 1. General Provisions ##

Regardless of more specific provisions in these requirements, CA Owners have an overarching responsibility to keep the information in the CCADB about themselves, their operations and their certificates accurate, and to make updates in a timely fashion. Minimally, CA Owners with certificates included in a participating Store must ensure their information stored in the CCADB is kept up to date as changes occur.

All data in the CCADB may be made public or semi-public in a variety of forms; CA Owners should not place any information in the CCADB which they wish to keep confidential. Stores are not obliged to publish any CCADB information.

All client devices that are used to download Personally Identifiable Information from the CCADB should employ disk-based encryption.

## 2. Contact Information ##

CA Owners must provide the following information for a Primary Point of Contact (POC), and at least one other POC, who may or may not be a Primary POC:

* Name
* Office email address

CA Owners may optionally designate further POCs, supplying an email address for each. CA Owners must also supply at least one non-personal contact email aliases which are more likely to continue working as personnel change; these are maintained as part of the CA’s organizational entry.

All Primary POCs should be authorized to speak for and enter into binding commitments on behalf of the CA(s) that they represent. The Primary POC will be issued a [CA Community license](https://www.ccadb.org/cas/request-access#application-for-ccadb-access) and may request additional licenses for other Primary POCs. Primary POCs are responsible for keeping CCADB data accurate for their CA(s).

Notification of security and audit-related issues will be emailed to all Primary POCs and the first non-personal contact email alias. CA Owners are advised to make sure those addresses reach sufficient people such that they can respond to an issue in an appropriate timeframe.

If POC information needs to be updated, the CA Owner must submit an [Add/Update Contacts Case](https://www.ccadb.org/cas/contacts).

## 3. Root CA Certificates ##

A root CA certificate is a self-signed certificate issued by the root CA to identify itself and to facilitate verification of certificates issued to its subordinate CAs. CA Owners are responsible for maintaining correct and current information about their root CA certificates.

If root CA certificate information needs to be updated, the CA Owner must submit an [Add/Update Root Request Case](https://www.ccadb.org/cas/updates).

## 4. Subordinate CA Certificates ##

A subordinate CA certificate is a certificate signed by a root CA or another subordinate CA. The CCADB considers the terms “intermediate” and “subordinate” synonymous. To determine which subordinate CA certificates must be entered into the CCADB, refer to the individual Store policy. This includes certificates that are revoked. For newly-created subordinate CA certificates, this must happen before the certificate begins issuing publicly-trusted certificates.

Each instance (i.e. PEM data) of a subordinate CA certificate only needs to be included in the CCADB once.

If a subordinate CA certificate is revoked, the CCADB must be updated to mark it as revoked, including the reason for revocation, within seven calendar days of revocation. 

## 5. Policies, Audits, and Practices ##

CCADB enables associating Certificate Policy (CP) and/or Certification Practice Statement (CPS) documents in the records for both root CA certificates and subordinate CA certificates. CA Owners must provide at least an authoritative English version of any CP, CPS, or combined CP/CPS which are not originally in English, with version numbers matching the document they are a translation of.

CCADB also enables associating statements of attestation of CA Owner conformance to various requirements and other operational criteria (“audits”).

These documents are hosted elsewhere and the URLs are stored in the CCADB. The URLs to such CPs, CPSes and audits, and any metadata about them such as the name of the auditor or the date of the audit, must be updated as new information becomes available. For technical reasons, URLs to audit statements must point to a PDF file that conforms to ALV and either WebTrust or Accredited Conformity Assessment Bodies’ Council (ACAB'c) formatting standards.

The entry for each subordinate CA certificate has checkboxes to indicate "Audits Same as Parent" and "CP/CPS Same as Parent". When those are checked, the details do not need to be duplicated from the parent certificate. However, the subordinate CA certificate must be specifically listed in the audit statements of the parent certificate.

URLs for the following documents are required for each certificate, unless the exceptions below apply:

* CP
* CPS
* Standard audit (WebTrust or ETSI)
* Baseline Requirements (BR) audit (if the certificate is capable of issuing TLS/SSL server certificates)
* Extended Validation (EV) SSL and/or Code Signing audit (if applicable)

Exceptions to providing these documents:

* The SHA-256 fingerprint of the certificate is specifically listed as in scope in the audit statements of the parent certificate, and the "Audits Same as Parent" checkbox is checked; or
* The certificate is issued and managed under the same CP, CPS, or CP/CPS and the “CP/CPS Same as Parent” checkbox is checked; or
* The certificate has expired; or
* The certificate has been revoked, and the corresponding record in the CCADB has been updated with the correct revocation status.

CA Owners must submit an [Add/Update Root Request Case](https://www.ccadb.org/cas/updates) to add or update these documents for root CA certificates stored in the CCADB.

CA Owners must add or update these documents for subordinate CA certificates directly on the record in CCADB (unless the exceptions stated above apply).

### 5.1 Audit Statement Content ###

An authoritative English language version of publicly available audit information must be uploaded to the CCADB no later than three months after the end of the audit period. In the event of a delay greater than three months, the CA Owner must provide an explanatory letter signed by the Qualified Auditor. 

Reports uploaded to the CCADB must be publicly available and contain at least the following clearly-labeled text-searchable information: 

1. Full name of the CA Owner or corresponding Affiliate (e.g., organization providing external RA services) that was audited;
2. Name and address of the organization performing the audit;
3. Qualifications of the team performing the audit;
4. SHA-256 fingerprint of each root and subordinate CA certificate that was in scope of the audit (see format specifications below);
5. Full names and version numbers of the audit standards that were used during the audit;
6. List of the CA Owner's applicable policy documents (with version numbers and publication dates) referenced during the audit;
7. Whether the audit is for a period of time or a point in time;
8. Start date and end date of the period that was audited, for those that cover a period of time (this is not the period the auditor was on-site);
9. Point-in-time date, for those that are for a point in time;
10. Date the audit statement was written, which will necessarily be after the audit period end date or point-in-time date (see date format specifications below);
11. For ETSI, a statement to indicate if the audit was a full audit, and which parts of the criteria were applied, e.g. DVCP, OVCP, NCP, NCP+, LCP, EVCP, EVCP+, QCP-w, Part1 (General Requirements), and/or Part 2 (Requirements for trust service providers), and a statement to indicate that the auditor referenced the applicable CA/Browser Forum criteria and the version used;
12. All incidents disclosed by the CA Owner, or reported by a third party, and all findings reported by an auditor, that, at any time during the audit period, occurred, were open in Bugzilla, or were reported to a Store; and
13. An explicit statement indicating the audit covers the relevant systems and processes used in the issuance of all Certificates that assert one or more of the policy identifiers listed below:

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

#### 5.1.1 ETSI ####

Audits conducted by an accredited Conformity Assessment Body (CAB) must have their Audit Attestation Letter (AAL) uploaded to the CAB’s website. CA Owners provide the URL to the AAL on the CAB’s website, and ALV will verify those URLs against a list of approved CAB websites. ETSI AALs must follow the latest version of the AAL template on the ACAB'c [website](https://www.acab-c.com/downloads/).

CCADB warns root store operators when the audit periods are not consecutive.

When the AAL cannot be posted on the CAB's website, the CA Owner may post the AAL on their own website or attach the attestation report to a [Bugzilla Bug](https://www.ccadb.org/cas/fields#uploading-documents) and provide that URL. The authenticity of the AAL will still need to be established by the CAB. 

Additionally, if required by the individual Store policy, any non-conformity and/or problem resulting in the failure of the ETSI Certificate’s issuance may be considered an incident and have an [Audit Incident Report](https://www.ccadb.org/cas/incident-report) created in a Bugzilla Bug prior to or within seven calendar days of the AAL’s issuance date.

#### 5.1.2 WebTrust ####

Unqualified WebTrust audit statements provided by licensed WebTrust practitioners must have a WebTrust Seal. Qualified WebTrust audit statements provided by licensed WebTrust practitioners should have a WebTrust Seal. Whether unqualified or qualified, CAs enter the URL of the WebTrust Seal into the CCADB, and upon saving the record, the CCADB automatically converts the URL to point to the corresponding PDF file via integration with CPA Canada.

For qualified WebTrust audits, if a Seal is not obtained from CPA Canada, then the CA Owner must post the audit statement on their own website or attach the audit statement to a [Bugzilla Bug](https://www.ccadb.org/cas/fields#uploading-documents) and provide that URL. The authenticity of any WebTrust audit statement not provided with a Seal from CPA Canada will still need to be established with the auditor.

Additionally, if required by the individual Store policy, any qualification and/or modified opinion may be considered an incident and have an [Audit Incident Report](https://www.ccadb.org/cas/incident-report) created in a Bugzilla Bug prior to or within seven calendar days of the audit statement’s issuance date. 

#### 5.1.3 ALV Formatting ####

CCADB uses an application called Audit Letter Validation (ALV) to automatically parse and validate audit statements. This system eliminates manual processing, but it requires audit statements to follow some basic rules in order to function properly. If the audit statement fails to meet any of the following requirements, the CA Owner must work with their auditor to provide an audit statement that passes ALV.

Format Specifications for SHA-256 Fingerprints:

* MUST: No colons, no spaces, and no line feeds
* MUST: Uppercase letters
* MUST: Be encoded in the document (PDF) as text searchable, not an image

Format Specifications for Dates: The following formats are accepted by ALV
* Month DD, YYYY example: May 7, 2016
* DD Month YYYY example: 7 May 2016
* YYYY-MM-DD example: 2016-05-07
* Month names in English
* No extra text within the date, such as “7th” or “the”

ALV supports the following format for specifying audit period date ranges:
<br>
```<date><space><splitter><space><date>```
<br>
Where splitter must be one of the following:
* to
* through
* until
* and
* \-
* \~

### 5.2 Audit Firm and Audit Team Qualifications ###

CA Owners must ensure audits used to comply with this policy are performed by entities licensed or otherwise permitted to provide assurance services in the country(ies) where the assessment is performed, for the entirety of the audit engagement’s duration.

#### 5.2.1 Audit Team Qualifications ####

Each audit statement must be accompanied by documentation of the audit team qualifications sufficient to determine the competence, experience, and independence of the auditor. This documentation may be part of the audit statement, or may be provided as a separate text-searchable PDF file, and must contain the following information:

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

### 5.3 Annual CCADB Self-Assessments ###

Some Store policies may require the completion of an annual [self-assessment](https://www.ccadb.org/cas/self-assessment) using the CCADB template at various times to evaluate the conformance of the CA Owner’s policies against industry policies and practices.

If an annual CCADB self-assessment is required by the individual Store policy, a single self-assessment may cover multiple CAs operating under both the same CP and CPS(s), or combined CP/CPS. CAs not operated under the same CP and CPS(s) or combined CP/CPS must be covered in a separate self-assessment.

The self-assessment submission date is determined by the earliest appearing “BR Audit Period End Date” field specified in any of the CA Owner’s “CA Owner/Certificate” CCADB root records that are included in one or more Stores. 

An annual self-assessment must be completed and submitted to the CCADB within 92 calendar days from the CA Owner's earliest appearing root record “BR Audit Period End Date” that is after December 31, 2023. CA Owners should submit the self-assessment to the CCADB at the same time as uploading audit reports.

CA Owners should always use the latest available version of the self-assessment template. CA Owners must not use a version of the self-assessment template that has been superseded by more than 90 calendar days before their submission.

## 6. Mailshots ##

From time to time, a Store may use the CCADB to send information to CA Owners. Mailshots will be sent to at least the Primary POC(s) and the email aliases, and may also go to one or more of the other POCs; the exact recipient list is defined by the Store sending the information.

-----

Any copyright in this document is [dedicated to the Public Domain](https://creativecommons.org/publicdomain/zero/1.0/).

[CCADB-Audit-Case]:    https://ccadb.org/cas/updates
