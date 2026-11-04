# CCADB Field Reference and Valid Values

This reference explains how certificate, audit, policy, revocation, automation, and system-generated fields in the CCADB are populated and validated.

> **Where Fields Are Edited in the CCADB:**
> - **Root CA certificates:** Maintained through a staged [Add/Update Root Request](updates) case (**AUDITS**, **NON-AUDIT DOCUMENTS**, **ROOT INFORMATION**, **TEST WEBSITES**, and **EXAMPLE CERTIFICATES** tabs) and reviewed by a Root Store Operator before syncing to the live root record.
> - **Intermediate (subordinate) CA certificates:** Edited directly on the certificate record by the CA Owner; see [Managing Intermediate Certificates](intermediates). *(Note: The CCADB treats the terms "intermediate" and "subordinate" as synonymous.)*

## Table of Contents

1. [Certificate Ownership and Hierarchy Fields](#certificate-ownership-and-hierarchy-fields)
2. [PEM Data](#pem-data)
3. [Audit Information](#audit-information)
4. [Auditor Information](#auditor-information)
5. [Non-Audit Information (Policy & Self-Assessment Documents)](#non-audit-information)
6. [Revocation and CRL Information](#revocation-information)
7. [Issuance, Policy Identifier, and Automation Fields](#issuance-policy-identifier-and-automation-fields)
8. [System-Generated Fields](#system-generated-fields)
9. [Uploading Documents (Bugzilla Fallback)](#uploading-documents)

---

## Certificate Ownership and Hierarchy Fields

| Field Name | Applies To | What to Enter |
|---|---|---|
| `Certificate Name` | Root & Intermediate | Defaults to the certificate's Subject Common Name (`CN`), or Subject Organization (`O`) if `CN` is absent. CA Owners may edit this field on intermediate certificate records. |
| `Parent CA Owner/Certificate` | Intermediate | Must identify the issuing root or intermediate CA certificate record in the CCADB. |
| `Subordinate CA Owner` | Intermediate | Per [CCADB Policy Section 3.2](../policy#32-subordinate-ca-certificates), enter the subordinate CA Owner's exact organization name **as it appears in the provided audit statements**. **Do not leave this field blank** unless *both* private key control and domain/IP validation activities are performed by the organization named in the parent certificate's audit statement. *(Mismatches here cause `CA Owner Not Found` errors in [ALV](ALV#common-alv-findings).)* |

---

## PEM Data

The CCADB accepts X.509 certificates encoded in textual **PEM** format ([RFC 7468](https://datatracker.ietf.org/doc/html/rfc7468)) when adding [root certificates](updates#adding-or-selecting-root-certificates-addselect-root-certificates), [intermediate certificates](intermediates#adding-intermediate-certificate-data), or [example end-entity certificates](updates#example-certificates).

### Formatting Requirements
- Paste a **single** Base64-encoded certificate bounded strictly by `-----BEGIN CERTIFICATE-----` and `-----END CERTIFICATE-----`.
- Do **not** include private keys, certificate chains (multiple concatenated PEM blocks), leading/trailing metadata text, or extra blank lines inside the Base64 body.
- You can inspect and verify your PEM encoding before uploading with the [CCADB Certificate Viewer](https://certviewer-dot-ccadb-231121.appspot.com/certviewer).

---

## Audit Information

Depending on the trust purposes (EKUs) of a CA hierarchy, up to **seven** audit statement categories may be disclosed in the CCADB (see the required audit mapping table in [CCADB Policy Section 5](../policy#5-audit-disclosures) and content rules in [Section 5.2](../policy#52-audit-statement-content)):

1. **Standard Audit**
2. **Network Security (`NetSec`) Audit**
3. **TLS Baseline Requirements (`TLS BR`) Audit**
4. **TLS EV Guidelines (`TLS EVG`) Audit**
5. **Code Signing Audit** *(required for Code Signing and Time Stamping hierarchies)*
6. **S/MIME Baseline Requirements (`S/MIME BR`) Audit**
7. **Verified Mark Certificate (`VMC`) Audit** *(where applicable under Mark Certificate Requirements)*

Publicly available English-language audit statements must be submitted to the CCADB **no later than 92 calendar days** after the audit period end date (or point-in-time date). If an audit statement cannot be provided within 92 calendar days, upload a signed explanatory letter from the Qualified Auditor to the Bugzilla [CA Documents component](https://bugzilla.mozilla.org/buglist.cgi?product=CA%20Program&component=CA%20Documents) before the 92-day deadline.

| Field Name | What to Enter |
|---|---|
| `Audits Same as Parent` *(Intermediate records only)* | Check this box if the intermediate certificate is covered by (and its SHA-256 fingerprint is explicitly listed in) the current, or, if newly issued after the parent's latest audit period, next—audit statements of its issuing parent certificate. When checked, leave all other audit fields on the intermediate record blank. Uncheck if providing separate audit statements. |
| `Audit Statement (Link)` / `* Audit URL` | Direct HTTPS URL to a text-searchable PDF conforming to [ALV formatting rules](../policy#523-alv-formatting):<br>• **WebTrust Seals:** Enter the CPA Canada WebTrust Seal URL; upon saving, CCADB automatically converts it to the corresponding CPA Canada PDF URL. (For qualified WebTrust reports without a Seal, host the PDF on your website or [attach it to Bugzilla](#uploading-documents).)<br>• **ETSI Audits:** Enter the direct PDF URL to the Audit Attestation Letter (AAL) hosted on the Conformity Assessment Body's (CAB's) website following the latest [ACAB'c AAL template](https://www.acab-c.com/downloads/). |
| `Audit Type` | Select the option that matches the audit criteria performed (typically `WebTrust` or `ETSI EN 319 411`, or an approved equivalent). |
| `Audit Statement Date` | Date the audit report was signed/issued (`report date` for WebTrust; `issuing date` for ETSI AALs).<br>• **Revised / Corrected Reports:** Per [CCADB Policy Section 5.2(11)](../policy#52-audit-statement-content), if an audit report is reissued solely to fix formatting, omissions, or errors without changing the audit scope or period, you may retain the initial issuance date (ensure the PDF states both dates, link to the latest PDF, and explain the revision date/reason in a Case Comment). |
| `Audit Period Start Date` & `Audit Period End Date` | First and last day of CA operations covered by the audit engagement (**not** the dates the auditors were on-site). CA operations must be covered by an unbroken sequence of audit periods, and no single period may exceed one year. (Point-in-time readiness audits are reviewed manually when applicable.) |
| `Audit Team Qualifications` *(Root Case `AUDITS` tab)* | Required per [CCADB Policy Section 5.3.1](../policy#531-audit-team-qualifications). If auditor team qualifications are not embedded inside the audit report PDF itself, upload the separate text-searchable PDF on the **AUDITS** tab. |

---

## Auditor Information

Auditor qualifications are verified and maintained in the CCADB by Root Store Operators (see [For Auditors](../auditors) and [CCADB Policy Section 5.3](../policy#53-audit-firm-and-audit-team-qualifications)).

| Field Name | What to Enter |
|---|---|
| `Auditor` & `Auditor Location` | View recognized audit firms and office locations via the **Auditors** / **List All Audit Firms** report link on any root, intermediate, or case page.<br>• To populate either field, click the **pencil icon**, type two or more characters of the firm name or office location, press **Return**, select the matching entry, and click **Save**.<br>• If your audit firm or office location is missing from the list, contact `support [at] ccadb [dot] org` or your reviewing Root Store Operator. |

---

## Non-Audit Information

Policy disclosures are governed by [CCADB Policy Section 4](../policy#4-policy-disclosures), and annual self-assessments by [Section 6.4](../policy#64-annual-ccadb-self-assessments) (see [CCADB Self-Assessment](self-assessment)). Updated policy documents should be submitted to the CCADB within **7 calendar days** (and **must** be submitted within **14 calendar days**) of their effective date.

On **Root Certificate** records, policy documents and self-assessments are added and superseded on the [NON-AUDIT DOCUMENTS](updates#non-audit-documents) tab of an **Add/Update Root Request** case. On **Intermediate Certificate** records (which are neither expired nor revoked), populate the fields below:

| Field Name | What to Enter |
|---|---|
| `Policy Documentation` | Optional notes about the disclosed documents (e.g., authoritative language notes or supplemental policy references). |
| `CA Document Repository` | Public URL to the CA's online policy and certificate repository pertaining to this certificate. |
| `CP Same as Parent`, `CPS Same as Parent`, `CP/CPS Same as Parent`, `MD/AsciiDoc CP/CPS Same as Parent`, `Self-Assessment Same as Parent` | *(Intermediate records only)* Check the applicable box(es) if this intermediate certificate is governed by the exact same document (or a subset) disclosed on its issuing parent certificate. When checked, leave the corresponding URL and Effective Date fields blank. Uncheck to enter a subordinate-specific document. |
| `Certificate Policy (CP) URL`, `Certification Practice Statement (CPS) URL`, `Certificate Practice & Policy Stmt URL`, `MD/AsciiDoc CP/CPS URL`, `Self-Assessment URL` | Direct, unauthenticated URL to the document specific to this certificate (required whenever the corresponding `* Same as Parent` box is unchecked). If hosting on your own repository is not possible, see [Uploading Documents](#uploading-documents). |
| `CP Effective Date`, `CPS Effective Date`, `CP/CPS Effective Date`, `MD/AsciiDoc CP/CPS Effective Date`, `Self-Assessment Effective Date` | Effective/publication date of the disclosed document (required whenever the corresponding `* Same as Parent` box is unchecked). |

---

## Revocation Information

### Revocation Status of This Certificate (Intermediate Records)

Per [CCADB Policy Section 3.2](../policy#32-subordinate-ca-certificates), if a subordinate CA certificate is revoked, its CCADB record **must** be updated within **7 calendar days** of revocation, and its CRL entry must include a `reasonCode` extension (revocations due to security concerns also require a confidential [Incident Report](incident-report#how-do-i-submit-a-security-sensitive-incident-report)).

| Field Name | What to Enter |
|---|---|
| `Revocation Status` | Select `Revoked` (or `Not Revoked` / `Parent Cert Revoked`, as applicable). See [Marking an Intermediate Certificate as Revoked](intermediates#marking-an-intermediate-certificate-as-revoked). |
| `Date of Revocation` | Exact revocation date matching the revocation entry in the issuing CA's CRL. |
| `RFC 5280 Revocation Reason Code` | Revocation reason code matching the `reasonCode` extension in the issuing CA's CRL. |
| `Alternate CRL` | Populate **only** if this certificate itself lacks a CRL Distribution Point (`cRLDistributionPoints`) extension. *(Note: CA/Browser Forum Baseline Requirements require subordinate CA certificates to include CRL URLs.)* |

<a id="pertaining-to-certificates-issued-by-this-ca"></a>
### CRL Disclosures for Certificates Issued by This CA

Per [CCADB Policy Section 6.2](../policy#62-certificate-revocation-list-disclosures), for every unexpired and unrevoked CA certificate in the CCADB, CA Owners must disclose all distinct HTTP `cRLDistributionPoints` URLs appearing in unexpired certificates issued by that CA at the earlier of **within 7 days of first issuance** or **within 4 hours of first revocation** using that URL:

| Field Name | What to Enter |
|---|---|
| `Full CRL Issued By This CA` | This field is not editable. It is automatically populated by a program that reads from `JSON Array of All Full CRL URLs` and collects the first URL presented in the JSON array. |
| `JSON Array of All Full CRL URLs` | Properly formatted JSON array of all distinct full CRL HTTP URLs appearing in unexpired certificates issued by this CA even if there is only a single URL.<br>• Example (single): `["http://crl.example.com/ca1.crl"]`<br>• Example (multiple): `["http://crl1.example.com/ca1.crl","http://crl2.example.com/ca1.crl"]`<br>• All listed Full CRL URLs must serve an identical CRL and should **not** contain an `IssuingDistributionPoint` extension. |
| `JSON Array of Partitioned CRLs` | When the CA uses partitioned (sharded) CRLs instead of a full CRL, leave `JSON Array of All Full CRL URLs` blank and enter a JSON array of all partial DER-encoded CRL URLs whose union covers all unexpired certificates issued by this CA:<br>• Example: `["http://cdn.example.com/crl-1.crl","http://cdn.example.com/crl-2.crl"]`<br>• Each partitioned CRL **must** contain a critical `IssuingDistributionPoint` extension whose `distributionPoint` `UniformResourceIdentifier` **exactly matches** the disclosed URL.<br>• **Pre-issuance placeholder:** If an unrevoked CA certificate has **not yet issued any certificates**, enter `[""]` in `JSON Array of Partitioned CRLs` until issuance begins. |

---

## Issuance, Policy Identifier, and Automation Fields

These fields appear under **Pertaining to Certificates Issued by This CA** on intermediate certificate records (and corresponding sections on root records):

| Field Name | What to Enter |
|---|---|
| `CA/B Forum Certificate Policy Identifier` | Select all CA/Browser Forum Certificate Policy OIDs (e.g., `2.23.140.1.2.1`, `2.23.140.1.2.2`, `2.23.140.1.1`) that may be asserted in certificates issued by this CA. |
| `ACME Directory URL(s)` | If this CA issues TLS server authentication certificates and supports ACME, enter one or more ACME Directory endpoint URLs. Separate multiple URLs with a semicolon (`;`). |
| `Other Automated Solution Description` | If this CA supports a non-ACME automated certificate management solution for TLS server authentication certificates, enter one or more URLs to public documentation describing the capability and how subscribers can use it. Separate multiple URLs with a semicolon (`;`). |
| `Automation Test Certificate Website` | Enter the URL of an active test website serving a valid TLS certificate issued via your ACME or non-ACME automation solution for each applicable CA/Browser Forum certificate type issued by this CA. Separate multiple URLs for the same certificate type with a semicolon (`;`). |

---

<a id="formula-fields"></a>
<a id="system-generated-fields"></a>
## System-Generated Fields

The fields below are calculated automatically by CCADB triggers or daily batch jobs and **cannot be manually edited**. Root Store Operators and [ALV](ALV#intermediate-certificates) use these fields to determine which audits and disclosures are required for each certificate in a hierarchy:

| Field Name | Logic | Updates |
|---|---|---|
| `Derived Trust Bits` | <ul><li>Set to empty when the certificate is expired or revoked, or when the root certificate that the intermediate certificate chains up to is not included in any root stores.</li><li>Directly map to Extended Key Usage (EKU) values when the certificate's EKU is present and not empty.</li><li>If the EKU is empty or not present, then set "Derived Trust Bits" to the union of the trust-bits/EKUs that are on the parent root certificate for each root store that it is included in.<ul><li>Check for same Subject+SPKI root certificates, and if found, update the union to add the trust-bits/EKUs that are on the parent root certificate for each root store that it is included in (if not already in the union).</li></ul></li></ul><ul><li>If this certificate has an intermediate certificate as its parent in the CCADB, then:<ul><li>Create "List2" that consists of the parent certificate’s "Derived Trust Bits" unioned with the "Derived Trust Bits" of all of the parent certificate’s unexpired unrevoked same Subject+SPKI certificates.</li><li>Remove anything from this certificate's "Derived Trust Bits" that is not in "List2".</li></ul></li></ul> | When related fields are updated on a root or intermediate certificate record, a trigger method launches an asynchronous process that updates this field (if needed) for every certificate within that record's CCADB hierarchy. |
| `EV SSL Capable` | For an intermediate certificate to be considered technically capable of issuing EV SSL certificates, all of the following have to be true for that certificate as well as the intermediate certificates that it chains up to.<ol><li>The certificate is not revoked and not expired.</li><li>"Derived Trust Bits" field contains "Server Authentication"</li><li>The root certificate that it chains up to is enabled for EV by at least one of the root stores that it is included in.</li><li>"Policy Identifiers" field contains one or more of 2.23.140.1.1, 2.5.29.32.0, or any of the values in the ExtendedValidation.cpp OIDs field of the root certificate.</li></ol>If the above check fails for a parent intermediate certificate, then look for unexpired unrevoked same Subject+SPKI certificates and perform the check on any that are found. | When related fields are updated on a root or intermediate certificate record, a trigger method launches an asynchronous process that updates this field (if needed) for every certificate within that record's CCADB hierarchy. |
| `Technically Constrained` | <ul><li>Set to FALSE if the certificate does not contain an Extended Key Usage (EKU) extension.</li><li>Set to TRUE if the EKU does not contain id‐kp‐serverAuth or anyExtendedKeyUsage.</li><li>If the EKU contains id‐kp‐serverAuth, then set to TRUE if the certificate includes the Name Constraints X.509v3 extension with constraints on dNSName, iPAddress and DirectoryName. Otherwise set to FALSE.</li></ul> | Set when certificate PEM is imported into the CCADB. |
| `Has Non-constrained SS+SPKI?` | This field is set to TRUE when its "Technically Constrained" field is set to TRUE and there are unexpired unrevoked same Subject+SPKI intermediate certificates that have Technically Constrained == FALSE. | A batch program runs once per day to update this flag. |

---

<a id="uploading-documents"></a>
## Uploading Documents (Bugzilla Fallback)

Policy documents (`CP`, `CPS`, `CP/CPS`), self-assessments, and audit statements should normally be hosted directly on the CA Owner's website, the subordinate CA Owner's website, CPA Canada, or the auditor's website.

When direct hosting is not possible (for example, when uploading **preliminary audit statements for [ALV testing](ALV#testing-audit-statements-with-alv)**, qualified WebTrust audits without a CPA Canada Seal, ETSI AALs that cannot be hosted on the CAB's site, or 92-day audit delay letters), you may attach the file to a Mozilla Bugzilla bug in the `CA Documents` component and use the direct attachment URL in CCADB:

1. If you do not already have a Mozilla Bugzilla account, [create an account](https://bugzilla.mozilla.org/createaccount.cgi).
2. [Search existing `CA Documents` bugs](https://bugzilla.mozilla.org/buglist.cgi?query_format=advanced&product=CA%20Program&component=CA%20Documents) to check whether a document-storage bug already exists for your CA.
3. If none exists, [file a new `CA Documents` bug](https://bugzilla.mozilla.org/enter_bug.cgi?product=CA%20Program&component=CA%20Documents):
   - **Summary:** `Documents for <Your CA Name>`
   - **Description:** `The purpose of this bug is to store documents related to the root and intermediate certificates for <Your CA Name>.`
4. Attach your PDF or document to that bug using **Attach New File**.
5. Copy the **direct link to the attachment** (not the bug comment page URL) and paste it into the corresponding URL field in the CCADB.
6. Reuse that same Bugzilla bug for any future document attachments for your CA.
