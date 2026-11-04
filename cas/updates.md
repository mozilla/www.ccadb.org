# Managing CA Owner and Root Certificate Records

CA Owners use an **Add/Update Root Request** case in the CCADB to add new root CA certificate records or update existing CA Owner and root CA certificate information, including organizational details, annual audit statements, policy documents, and test websites.

## Overview: How CCADB Records Are Maintained

Certificates in the CCADB are organized into hierarchies: each **CA Owner** record has child **root certificate** records, which in turn have child **intermediate** (also referred to as **subordinate**) certificate records.

Because Root Store Operators review changes to CA Owner and root certificate data before those changes take effect, **CA Owners cannot directly edit live CA Owner or root certificate records**. Instead, updates follow a staged review workflow:

1. The CA Owner creates an **Add/Update Root Request** case and enters the desired additions or edits. All changes remain local to the case (`Case Request Status: CA Providing Data`) while in progress.
2. When all updates are entered, the CA Owner clicks **Submit to Root Store**.
3. A Root Store Operator reviews the requested changes and either approves/syncs them to the live CA Owner and root certificate records, or returns the case (`CA Providing Data`) with comments requesting clarification.

Use the table below to confirm you are using the right CCADB workflow before starting:

| What You Need to Add or Update | Where to Make the Change |
|---|---|
| **CA Owner organization details** (name, website, address, or CA email aliases) | Submit an **Add/Update Root Request** case (instructions on this page) |
| **Root CA certificates** (new root PEMs, root metadata, root audit statements, root policy documents, or test websites) | Submit an **Add/Update Root Request** case (instructions on this page) |
| **Intermediate / Subordinate CA certificates** (new PEMs, CRLs, intermediate audits, intermediate policy documents, or revocations) | Edit the certificate record directly; see [Managing Intermediate Certificates](intermediates) |
| **Individual Points of Contact (POCs) or CCADB login licenses** | Submit an **Add/Update Contacts** case; see [Managing Points of Contact](contacts) |
| **Root Store inclusion** (requesting trust in participating Root Store Programs) | First add the root via an **Add/Update Root Request** case, then submit a separate **Root Inclusion Request** case—see [Submitting a Root Inclusion Request](inclusion) |

All CA Owners must update audit, policy document, [self-assessment](self-assessment), and test website information for their certificate hierarchies **at least annually**, and keep CCADB records current within the timelines required by the [CCADB Policy](../policy).

## Table of Contents

1. [Creating an Add/Update Root Request Case](#1-creating-an-addupdate-root-request-case)
2. [Common Actions Across Tabs](#2-common-actions-across-tabs)
3. [Case Tabs Reference](#3-case-tabs-reference)
   - [CA OWNER](#ca-owner)
   - [AUDITS](#audits)
   - [NON-AUDIT DOCUMENTS](#non-audit-documents)
   - [ROOT INFORMATION](#root-information)
   - [TEST WEBSITES](#test-websites)
   - [EXAMPLE CERTIFICATES](#example-certificates)
   - [CASE PROGRESS](#case-progress)
4. [Submitting and Tracking Your Case](#4-submitting-and-tracking-your-case)
5. [Obsoleting Root Records](#5-obsoleting-root-records)

---

## 1. Creating an Add/Update Root Request Case

1. [Log in to the CCADB](https://ccadb.my.site.com/CustomLogin) (see [Getting Started](getting-started) if needed).
2. Click the **My CA** tab in the top navigation bar.
3. Click the **CASES** sub-tab under your CA Owner's name near the upper-left corner.
4. Click the **New** button on the right side of the page (below **Get URLs**).
5. Select **Add/Update Root Request** and click **Next**.
6. Enter a clear, descriptive **Subject** for the case, for example:
   - `Add <Root Name> Root Certificate`
   - `2026 Audit Statements for <CA Name>`
   - `May 2026 Policy Document Updates for <CA Name>`
7. Click **Save**.
8. Open your newly created case using any of the following methods:
   - Click the case number in the green confirmation banner across the top of the page (`Case ###### was created`).
   - Return to **My CA** → **CASES** and click the case number in the top row of the **Case** column.
   - Go to your CCADB **Home** page, expand **Open Cases** under **CA Task List**, and click the case number.

---

## 2. Common Actions Across Tabs

### Editing Fields
Click the **pencil icon** next to any editable field, or click the downward arrow (**▼**) on the right side of a section header and select **Edit** to edit all fields in that section. After clicking **Save**, any values modified within the case are highlighted in **bold blue text**.

### Previewing Your Edits (`Show Changes`)
Click the **Show Changes** button at the top of a tab to inspect a side-by-side comparison of **Source (Case)** data against the live **Target (CA Owner or Root Certificate)** record. Click **Go Back** to return to the tab.

### Adding or Selecting Root Certificates (`Add/Select Root Certificates`)
The **NON-AUDIT DOCUMENTS**, **ROOT INFORMATION**, and **TEST WEBSITES** tabs remain mostly blank until root certificates are associated with the case. Click **Add/Select Root Certificates** at the top of any of these tabs to open a pop-up window where you can:

- **Select Existing Root Certificates:** Click **Select Root Certificates**, check the box next to each root certificate you want to update in this case (expired roots appear in italics), click **Save**, and click **Go Back**.
- **Remove Root Certificates from the Case:** Click **Deselect Root Certificates**, check any root certificate you want to remove from the case, click **Save**, and click **Go Back**.
- **Add a New Root Certificate to the CCADB:**
  1. Click **Add Root Certificate to CCADB**.
  2. Paste the root certificate's [PEM data](fields#pem-data) (`-----BEGIN CERTIFICATE-----` to `-----END CERTIFICATE-----`) and click **Validate PEM**.
  3. Review the parsed certificate details; if validation succeeds, click **Create Root Certificate in CCADB**, then click **Go Back**.
  4. Complete all required fields for the new root in the **ROOT INFORMATION** tab (and other applicable tabs) before submitting the case.

> **Note:** Selecting or removing root certificates on one tab (including associating roots with audits on the **AUDITS** tab) automatically displays or removes those root certificates across the **NON-AUDIT DOCUMENTS**, **ROOT INFORMATION**, and **TEST WEBSITES** tabs.

---

## 3. Case Tabs Reference

An `Add/Update Root Request` case contains six tabs. You only need to make changes in the tabs relevant to your request, for instance, a mid-year CP/CPS update typically only requires updating **NON-AUDIT DOCUMENTS** (provided **ROOT INFORMATION** has already been completed for the selected roots).

### CA OWNER
Use this tab to update high-level organizational information for the CA Owner, organized into three sections:
- **CA Owner/Certificate Information:** `CA Owner Name` and `Alternate CA Name(s)` (`Status (CA Owner)` is system-maintained).
- **CA Organization Information:** `Company Website`, `Organizational Type`, non-personal group email aliases (`CA Email Alias 1` and `CA Email Alias 2`), `Geographic Focus`, and `Primary Market / Customer Base`.
- **CA Address Information:** Mailing address fields (`Street`, `City`, `State/Province`, `Zip/Postal Code`, etc.).

*(To add, update, or mark individual POCs as obsolete, submit an [Add/Update Contacts](contacts) case instead.)*

<a id="audit-case-workflow"></a>
### AUDITS
Use this tab when submitting new or revised audit statements for root CA certificates:
1. **Audit Firm & Location:** Edit the **Audit Firm** section and search/select your auditor and office location as listed in the **List All Audit Firms** report link at the top of the tab. (Contact `support [at] ccadb [dot] org` if your auditor or location is missing; any *"Re-Verify this audit firm qualifications"* warning is handled by the reviewing Root Store Operator.)
2. **Audit Team Qualifications:** If qualification details ([CCADB Policy Section 5.3.1](../policy#531-audit-team-qualifications)) are not embedded inside the audit report PDF itself, upload the separate Audit Team Qualifications PDF using the file upload icon.
3. **Audit Information Sections:** Populate each applicable section (**Standard**, **NetSec**, **TLS BR**, **TLS EVG**, **Code Signing**, **S/MIME BR** and **VMC**) per [Field Types: Audit Information](fields#audit-information) and select the **Applicable root certificates** for each. WebTrust Seal URLs entered into `Audit Statement (Link)` are automatically mapped to the CPA Canada PDF URL upon saving.
4. **Run Audit Letter Validation (ALV):** Click **Validate Audits [ALV]** and check **ALV Results Summary** at the bottom of the tab. Remediate any errors using [Common ALV Findings](ALV#common-alv-findings).
   - **Optional Preliminary Testing:** CA Owners are encouraged to [test preliminary audit statements with ALV](ALV#testing-audit-statements-with-alv) before final auditor sign-off (add `"Preliminary Audit Reports"` as a comment in **CASE PROGRESS** while testing, and `"Final Audit Reports"` once final URLs are entered).

### NON-AUDIT DOCUMENTS
Use this tab to disclose, update, or supersede policy and practice documents associated with selected root certificates including **CP**, **CPS**, combined **CP/CPS**, **MD/AsciiDoc CP/CPS**, **TSPS**, **[Self-Assessment](self-assessment)**, **PKI Disclosure Statement**, and **Other** documents (see [CCADB Policy Section 4](../policy#4-policy-disclosures) and [Field Types: Non-Audit Information](fields#non-audit-information)):
- **Adding a Document:** Click **Add Non-Audit Document**, choose the document type, select the applicable root certificates and Policy Identifiers (use semicolon-space `; ` separation in `Additional Policy Identifiers` for OIDs not yet in CCADB), enter the effective/document date, and provide a **direct, unauthenticated file URL**:
  - Links should retrieve the raw document directly without redirects, logins, or `.zip` archives.
  - GitHub-hosted Markdown/AsciiDoc policies should use the raw file URL (`https://raw.githubusercontent.com/...`) ending in `.md` or `.adoc`.
- **Superseding Outdated Documents:** Do not leave duplicate active documents of the same type on the same certificate. Click **▼** on the outdated document's header and set a **Document Superseded Date** (marked `**SUPERSEDED**`). Before case approval, you can revert an accidental change via **Make Effective**. After case approval, you can edit the `Superseded Date` by selecting `Show All` on the `Non-Audit Documents` tab of a root certificate record and clicking on the **pencil icon**.

### ROOT INFORMATION
Use this tab to add new root certificates and maintain root-level metadata across four editable sections for each selected root certificate:
- **Root CA Background:** `Explanation and Role` (why the root should be considered for public trust and its unique function), `Root Certificate Download URL` (direct PEM or DER link), and optional `Public Comments`.
- **CA CRL:** `Full CRL Issued By This CA` or `JSON Array of Partitioned CRLs` (see [CCADB Policy Section 6.2](../policy#62-certificate-revocation-list-disclosures)).
- **PKI Hierarchy:** Yes/No disclosures for cross-signing, externally operated subordinate CAs, and external RAs (and whether permitted by the CP/CPS); `Description of PKI Hierarchy`; `Intended Use Case(s) Served` (EKUs); `CA/B Forum Certificate Policy Identifiers`; and `TLS Certificate Domain Validation Method` values.
- **Key Generation:** `Key Generation Date`, `Key Generation Audit Report Date`, and `Key Generation Audit Report (Link)`.

> **Important — Submission Requirement:** You **cannot** click **Submit to Root Store** on a **[Root Inclusion Request](https://www.ccadb.org/cas/inclusion)** case until all required fields on the **ROOT INFORMATION** tab are populated for **every** root certificate included in the case (both newly added and pre-existing roots). Once populated for a root certificate, these fields only need to be updated when the underlying information changes.

### TEST WEBSITES
Use this tab when updating valid, expired, or revoked test website URLs, or when submitting updated audit statements for root certificates trusted for TLS server authentication:
- Ensure each test website server sends **only** the intended certificate chain for the specific self-signed root certificate being tested (leaf certificate → issuing intermediate CA(s) → optional self-signed root). **Do not** serve cross-signed CA certificates or extra chains, which will cause validation to fail.
- Click **Validate Test Websites** → **Re-run Validation** to verify chain building, revocation/expiration status, and certificate lint checks, confirming all roots appear under **Successful Test Websites** rather than **Failed Test Websites**.

### EXAMPLE CERTIFICATES 
Use this tab to provide one example end-entity (`cA=FALSE`) certificate per applicable certificate profile so Root Store Operators can confirm that issued certificates match the root's declared policies, profiles, and hierarchy:
- **Selecting Roots and Profile Types:** Click **Add/Select/Deselect Root Certificates** to choose the root certificate(s), then click **`+`** (**Add Profile Type**) on each root's header to add slot checklists for the applicable certificate categories (**TLS**, **Code Signing**, **S/MIME**, **VMC**, and **Other**). *(Caution: clicking **`✕`** on a category header permanently deletes all slots and submitted PEMs in that category for that root.)*
- **Completing Profile Slots:** Each slot card displays the profile's governing standard, expected Policy OID(s), and (if applicable) expected `businessCategory`. Click a slot's **pencil icon** to set one of three states:
  - **Submitted:** Paste the leaf certificate [PEM](fields#pem-data) into **PEM Content** and click **Validate PEM**. When all checks pass, the button changes to **Save** and the status sets to **Submitted**—click **Save**.
  - **Not Issued:** If your CA does not issue certificates for that profile, select **Not Issued** from **Slot status** (an explanatory note is optional) and click **Save**.
  - **Pending:** Default state when a certificate is not yet provided (you may save notes while keeping the slot **Pending**).
- **Automated PEM Validation Rules:** A slot cannot be saved as **Submitted** until **Validate PEM** confirms:
  1. **End-entity & EKU:** Valid PEM encoding with `cA=FALSE` and an Extended Key Usage consistent with the profile category.
  2. **Disclosed Issuer in Hierarchy:** The certificate's Authority Key Identifier (AKI) matches the Subject Key Identifier (SKI) of an [intermediate CA certificate disclosed in the CCADB](intermediates) under the same CA Owner.
  3. **Policy OID & Business Category:** Certificate `policyIdentifiers` (and subject `businessCategory`, where required, such as EV) match the profile's expected values.

### CASE PROGRESS
Use this tab to manage and track your case before and after submission:
- **Add Comment:** Communicate context, special instructions, or responses to the reviewing Root Store Operator.
- **Case Progress Table:** View `Case Opened` / `Case Closed` timestamps, edit the case `Subject` (pencil icon), and verify which tabs currently show `Data to Verify` vs. `No Data to Verify`.
- **Case Comments:** Read questions and status notes posted by Root Store Operators.

---

## 4. Submitting and Tracking Your Case

### Submitting to Root Store Operators
Once you have verified your changes across all applicable tabs, click the **Submit to Root Store** button in the upper-right corner of the case page. This places your case into the Root Store Operators' review queue.

*(Reminder: Clicking **Submit to Root Store** only submits your data updates for verification—it does **not** request root inclusion. See [Submitting a Root Inclusion Request](inclusion) for the inclusion process.)*

### Troubleshooting `Submit to Root Store` Errors
If required fields are missing for any root certificate in the case, clicking **Submit to Root Store** displays the error banner:

> `Error! Please check the warning message on "ROOT INFORMATION" tab before submitting the case to the Root Store.`

Open the **ROOT INFORMATION** tab, check the warning message beneath each root certificate's collapsible section header, fill in any missing required fields, save your edits, and click **Submit to Root Store** again.

### Root Store Operator Review & Follow-Up
- **Responding to Returned Cases (`CA Providing Data`):** If the reviewing Root Store Operator needs additional information or corrections, they will post a comment in **CASE PROGRESS** and set `Case Request Status` back to **CA Providing Data**. Make the requested updates, add a reply comment if helpful, and click **Submit to Root Store** again to re-submit.

## 5. Obsoleting Root Records

### Why We Obsolete Root Certificate Records (Instead of Deleting Them)
The CCADB serves as both an operations platform for participating Root Store Operators and a durable historical archive of publicly disclosed Certification Authority (CA) hierarchies and corresponding compliance artifacts. For this reason, the CCADB does not delete root certificate records. Deleting a root record requires substantial administrative effort, risks breaking relational integrity across subordinate certificates, cases, audit statements, policy documents, and file archives, and undermines ecosystem transparency.

However, in rare instances, a root certificate record exists in the CCADB due to an administrative mistake, duplication, or internal Root Store Operator testing. Keeping the record active in these cases creates reporting clutter, triggers inapplicable maintenance tasks, or causes confusion without providing legitimate transparency value. To address these cases without deleting historical data, the CCADB provides an administrator-only boolean attribute: `Status in CCADB obsoleted?`.

Because enabling this attribute suppresses the certificate from public CCADB reports, obsolescence is intentionally reserved for narrow, exceptional circumstances rather than routine certificate lifecycle transitions.

### When Root Certificate Records Are Obsoleted
A root certificate record may be marked as Obsoleted only when it is not included (and has no active inclusion request) in any participating Root Store, has no active or non-obsolete subordinate CA records chaining to it, and meets at least one of the following criteria:

1. The certificate was inadvertently uploaded to the CCADB (for example, an internal-only or out-of-scope root added by mistake) and was never intended for CCADB disclosure or public Root Store inclusion.
2. The record duplicates an existing CCADB root certificate entry or represents an internal CCADB test or placeholder record (such as Example CA test hierarchies).

The CCADB Steering Committee may periodically update these criteria as new operational needs are identified, provided that any expansion preserves ecosystem transparency and does not obscure unresolved compliance or continuing disclosure obligations. In all cases, the rationale for marking a root record as Obsoleted should be documented.
