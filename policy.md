# Common CCADB Policy #

*Version 1.2*

1. [General Provisions](policy#1-general-provisions)
2. [Contact Information](policy#2-contact-information)
3. [Root Certificates](policy#3-root-certificates)
4. [Subordinate Certificates](policy#4-subordinate-certificates)
5. [Policies, Audits, and Practices](policy#5-policies-audits-and-practices) <br>
5.1 [Audit Statement Content](policy#51-audit-statement-content) <br>
5.2 [Auditor Qualifications](policy#52-auditor-qualifications) <br>
5.3 [Notification of Cross-Certificate Issuance](policy#53-notification-of-cross-certificate-issuance)
6. [Mailshots](policy#6-mailshots)

Several Web PKI root store operators (“Stores”) have collaborated to create the Common Certification Authority Database (CCADB), a data repository of certificate and Certification Authority (CA) information. CAs who wish to be included in participating Stores will need to maintain certain information in the CCADB. This document explains what is required of CAs who are required by Store policy to use the CCADB.

Stores may have their own additional CCADB-related requirements. For each root certificate, CAs must comply with the additional requirements pertaining to the Stores which contain that certificate. Additional information on Store requirements can be found [here](https://www.ccadb.org/resources).

This policy does not cover how to obtain write access to the CCADB or how to use the CCADB’s web interface. Additional information covering these topics is available [here](https://www.ccadb.org/cas/).

## 1. General Provisions ##

Regardless of more specific provisions in these requirements, CAs have an overarching responsibility to keep the information in the CCADB about themselves, their operations and their certificates accurate, and to make updates in a timely fashion. Minimally, CAs with certificates included in a participating Store must ensure their information stored in the CCADB is kept up to date as changes occur. When a timeline is not defined for a requirement specified within this policy, updates must be submitted to the CCADB within 14 calendar days of being completed.

All data in the CCADB may be made public or semi-public in a variety of forms; CAs should not place any information in the CCADB which they wish to keep confidential. However, Stores are not obliged to publish any CCADB information.

All client devices that are used to download Personally Identifiable Information from the CCADB should employ disk-based encryption.

## 2. Contact Information ##

CAs must provide the following information for a Primary Point of Contact (POC), and at least one other POC, who may or may not be Primary:

* Name
* Office email address

CAs may optionally designate further POCs, supplying an email address for each. CAs must also supply one or two non-personal contact email aliases which are more likely to continue working as personnel change; these are maintained as part of the CA’s organizational entry.

All Primary POCs should be authorized to speak for and enter binding commitments on behalf of the CA that they represent. At least one of the Primary POCs must hold a [CA Community license](https://www.ccadb.org/cas/request-access#application-for-ccadb-access); other POCs may also apply to a Store to be issued one. Those Primary POCs with a CA Community license are ultimately responsible for keeping CCADB data up-to-date for their CA.

Notification of security and audit-related issues will be emailed to all Primary POCs and the first email alias. CAs are advised to make sure those addresses reach sufficient people such that they can respond to an issue in an appropriate timeframe.

If POC or email alias information needs to be updated, the CA must email support@ccadb.org.

## 3. Root Certificates ##

A root CA certificate is a self-signed certificate issued by the root CA to identify itself and to facilitate verification of certificates issued to its subordinate CAs. CAs must maintain correct and current information about their root certificates.

If root certificate information needs to be updated, the CA must submit an [Add/Update Root Request Case](https://docs.google.com/document/d/1ttmeeqO6WxDWe_deDNsGUgDO_LpsvoduFNZeHHMw_f8/edit).

## 4. Subordinate Certificates ##

A subordinate CA certificate is a certificate signed by a root CA or another subordinate CA. The CCADB considers the terms “intermediate” and “subordinate” synonymous. All subordinate CA certificates capable of chaining to a root CA certificate included in at least one participating Store must be added to CCADB within seven calendar days of issuance. This includes certificates that are revoked. 

Each instance (i.e. PEM data) of a subordinate certificate only needs to be included in the CCADB once.

If a subordinate certificate is revoked, the CCADB must be updated to mark it as revoked, including the reason for revocation, within seven calendar days of revocation.

## 5. Policies, Audits, and Practices ##

In the records for both root certificates and subordinate certificates, CAs must provide the Certificate Policy (CP) and/or Certification Practice Statement (CPS) documents relating to that certificate, along with any documentation published by the CA and referenced within either of the precding documents. CAs must also provide statements of attestation of their conformance to various requirements and other operational criteria (“audits”), those statements being made by a competent independent party or parties. 

These documents are hosted elsewhere and the URLs are stored in the CCADB. The URLs to such CPs, CPSes and audits, and any metadata about them such as the name of the auditor or the date of the audit, must be updated as new information becomes available. For technical reasons, URLs to audit statements must point to a PDF file.

The entry for each subordinate certificate has “Audits Same as Parent” and “CP/CPS Same as Parent” checkboxes. When those are checked, the details do not need to be duplicated from the parent certificate. However, the subordinate certificate must be specifically listed in the audit statements of the parent certificate.

URLs for the following documents are required for each certificate, unless the exceptions below apply:
* CP
* CPS
* Standard audit (WebTrust or ETSI)
* Baseline Requirements (BR) audit (if the certificate is capable of issuing TLS/SSL server certificates)
* Extended Validation (EV) SSL and/or Code Signing audit (if applicable)

Exceptions to providing audit information:
* The SHA-256 fingerprint of the certificate is specifically listed as in scope in the audit statements of the parent certificate, and the “Audits Same as Parent” checkbox is checked; or
* The certificate has expired; or
* The certificate has been revoked, and the corresponding record in the CCADB has been updated with the correct revocation status.

CAs must provide English versions of any CP, CPS and Audit documents which are not originally in English, with version numbers matching the document they are a translation of. The English version is not required to be authoritative in all cases of dispute, but the CA must attest that the translation is not materially different to the original.

CAs must submit an [Add/Update Root Request Case](https://docs.google.com/document/d/1ttmeeqO6WxDWe_deDNsGUgDO_LpsvoduFNZeHHMw_f8/edit) to add or update audit information for root CA certificates stored in the CCADB.

CAs must add or update audit information for subordinate CA certificates directly on the record in CCADB.

### 5.1 Audit Statement Content ###

CCADB uses an Audit Letter Validation (ALV) tool to automatically parse and validate audit statements. If the audit statement fails to meet any of the following requirements, the CA must work with their auditor to provide an audit statement that passes ALV.

Audit statements listed in the CCADB must contain at least the following clearly-labeled information in English:

1. Name and address of the organization performing the audit;
2. Full name of the CA that was audited;
3. SHA-256 fingerprint of each root and subordinate certificate that was in scope of the audit (see format specifications below);
4. List of the CA policy documents (with version numbers) referenced during the audit;
5. Whether the audit is for a period of time or a point in time;
6. Date the audit statement was written, which will necessarily be after the audit period end date or point-in-time date (see date format specifications below);
7. Start date and end date of the period that was audited, for those that cover a period of time (this is not the period the auditor was on-site);
8. Point-in-time date, for those that are for a point in time;
9. Full names and version numbers of the audit standards that were used during the audit; 
10. All incidents disclosed by the CA, discovered by an auditor, or reported by a third party, that, at any time during the audit period, occurred, were open in Bugzilla, or were reported to a Store; and
11. For ETSI, a statement to indicate if the audit was a full audit, and which parts of the criteria were applied, e.g. DVCP, OVCP, NCP, NCP+, LCP, EVCP, EVCP+, QCP-w, Part1 (General Requirements), and/or Part 2 (Requirements for trust service providers).

#### 5.1.1 ETSI 

Audits conducted by an accredited Conformity Assessment Body (CAB) must have their Audit Attestation Letter (AAL) uploaded to the CAB’s website. CAs provide the URL to the AAL on the CAB’s website, and ALV will verify those URLs against a known list of AAL locations.

When an ETSI Certificate cannot be issued, the CA must still provide an AAL such that there are no gaps between audit periods for consecutive audits. The CA may post the AAL on their own website or attach the attestation report to a [Bugzilla Bug](https://www.ccadb.org/cas/fields#uploading-documents) and provide that URL. Additionally, the CA must provide an incident report for each audit finding (i.e., non-conformity), and/or problem resulting in the failure of the ETSI Certificate’s issuance, in a Bugzilla Bug prior to or within seven calendar days of the audit attestation letter’s issuance date.

#### 5.1.2 WebTrust

Audits conducted by licensed WebTrust practitioners must have a WebTrust Seal. CAs enter the URL to the WebTrust Seal into the CCADB, and upon saving of the record, the CCADB automatically converts the URL to point to the corresponding PDF file via integration with CPA Canada.

For qualified WebTrust audits, the CA may post the audit statements on their own website or attach the audit statement to a Bugzilla Bug and provide that URL. Additionally, the CA must provide an incident report for each audit finding (i.e., qualification) in a Bugzilla Bug prior to or within seven days of the audit letter’s issuance date.

#### 5.1.3 ALV Formatting

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

### 5.2 Auditor Qualifications ###

CAs must submit a summary of the Audit Team's qualifications and experience as outlined below with respect to the audit. The information can also be provided as part of the audit result documentation, like the [ETSI AAL](https://www.acab-c.com/downloads/), or as a supplement to the WebTrust Assurance Report.

* Date that the audit report was signed,
* Full name of the CA that was audited,
* Name and address of the audit firm or CAB,
* Audit Criteria, e.g. ETSI / WebTrust,
* Name of Lead Auditor (except where prohibited by law, otherwise, we ask that you not provide any personally identifiable information),
* For the Audit Team and the Audit Quality Reviewer, qualification information such as:
    * Number of Audit Team Members,
    * Academic qualifications or professional training received,
    * Average Years of Auditing Experience auditing trust services or similar information systems,
    * Experience, Special Skills, and Qualifications (e.g. audit/assessment principles and functions, information technology, software development, trust services, public key infrastructure, CA operations, and information security including risk assessment/management, network security, physical security, etc.), and
    * Credentials, Designations, or Certifications (e.g. CPA, CISA, CITP, CISSP, CCSP/CCA/CCP, etc.).
* How the Audit Team and team members are bound by law, regulation or professional standards to render an independent assessment of the CA (e.g.https://pub.aicpa.org/codeofconduct/Ethics.aspx# 0.300.050 Objectivity and Independence; CPA Canada, Rule 204; or Annex A of ETSI EN 319 403/403-1, respectively),
* Name of the Insurance Carrier providing the professional liability or errors and omissions insurance coverage defined in CA/B Forum Baseline Requirements section 8.2., and
* Whether the Audit Team relied on any third-party specialists or affiliate audit firms, and if so, their names and where they performed services.

### 5.3 Notification of Cross-Certificate Issuance ###

CAs must notify public@ccadb.org at least three weeks before issuing a new or replacement cross-certificate that can validate to a corresponding root CA certificate in one of the Stores. Individual Stores Program policies may require express approval before cross-certificate issuance. Corresponding Stores may choose to express cross-certificate issuance approval to the CA directly or through public@ccadb.org.

When announcing the intent to issue a new cross-certificate, the signing CA must include:

* the intended issuing CA certificate’s SHA-256 hash,
* the intended subject CA certificate’s DN,
* the intended date of certificate issuance,
* whether the cross-certificate is replacing an existing certificate,
* the organization responsible for operating the intended subject CA,
* the organization that owns the intended subject CA’s key material,
* the organization providing RA services for the intended subject CA, and
* all relevant audit reports related to the intended subject CA (if not already included in CCADB).

Additionally, when the intent to issue a new or replacement cross-certificate includes issuance to a CA owned or operated by a different CA owner, the signing CA must also include:

* a detailed description of the process the intended issuing CA used to evaluate the conformance of the intended subject CA and subject CA against its own policies, the Baseline Requirements, and this policy,
* all relevant artifacts related to the evaluation of the intended subject CA and subject CA (including CP, CPS, subscriber agreements, assessment methodology, outputs from the assessment process, assessor qualifications, etc.), and
* a detailed description of the intended issuing CA’s planned compliance monitoring activities and oversight functions for the intended subject CA.

## 6. Mailshots ##

From time to time, a Store may use the CCADB to send information to CAs.
Mailshots will be sent to at least the Primary POC and the email aliases, and may also go to one or more of the other POCs; the exact recipient list is defined by the Store sending the information.

-----

Any copyright in this document is
[dedicated to the Public
Domain](https://creativecommons.org/publicdomain/zero/1.0/).
