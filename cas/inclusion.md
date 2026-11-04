# Submitting a Root Inclusion Request

CA Owners use a **Root Inclusion Request** case in the CCADB to request that one or more of their root CA certificates be included in one or more participating Root Store Programs (**Apple**, **Google Chrome**, **Microsoft**, and **Mozilla**).

Submitting a `Root Inclusion Request` case does not guarantee inclusion. Each Root Store Operator evaluates requests independently according to its own [Root Store Program policy and timeline](../resources#root-store-information).

> **Ongoing Record Maintenance vs. Inclusion Requests:** Use a **Root Inclusion Request** case only to apply for root inclusion or update program-specific fields for that inclusion request. Continue using an [Add/Update Root Request](updates) case for all ongoing updates to CA Owner details, annual audit statements, policy documents, example certificates, and test websites.

## Table of Contents

1. [Prerequisites Before Requesting Inclusion](#1-prerequisites-before-requesting-inclusion)
2. [Creating a Root Inclusion Request Case](#2-creating-a-root-inclusion-request-case)
3. [Selecting Root Certificates and Root Store Programs](#3-selecting-root-certificates-and-root-store-programs)
4. [Completing Root Store Program Tabs](#4-completing-root-store-program-tabs)
   - [Shared Per-Root Fields](#shared-per-root-fields)
   - [Apple](#apple)
   - [Google Chrome](#google-chrome)
   - [Microsoft](#microsoft)
   - [Mozilla](#mozilla)
5. [Submitting and Tracking Your Request (`CASE PROGRESS`)](#5-submitting-and-tracking-your-request-case-progress)

---

## 1. Prerequisites Before Requesting Inclusion

Before you can select a root CA certificate in a **Root Inclusion Request** case (or enter a [Root Inclusion Public Discussion](public-group#root-inclusion-public-discussion)), ensure the following prerequisites are complete:

1. **CCADB Account Access:** Your organization must have an active CCADB account (see [Request Access](request-access) and [Getting Started](getting-started)).
2. **Completed `Add/Update Root Request` Case:** You must first add the root CA certificate to the CCADB and have a Root Store Operator approve and sync one or more [Add/Update Root Request](updates) cases containing all required disclosures across:
   - **CA OWNER** (organization details and email aliases)
   - **AUDITS** (audit statements and ALV validation)
   - **NON-AUDIT DOCUMENTS** (CP/CPS and [CCADB Self-Assessment](self-assessment))
   - **ROOT INFORMATION** (Root CA Background, Full/Partitioned CRLs, complete **PKI Hierarchy** disclosures, and **Key Generation** audit report)
   - **TEST WEBSITES** and **EXAMPLE CERTIFICATES** (where applicable to the hierarchy's intended use cases)
3. **Subordinate CA Disclosures:** All subordinate (intermediate) CA certificates chaining to a root certificate associated with a `Root Inclusion Request` must be disclosed in the CCADB per [CCADB Policy Section 3.2](../policy#32-subordinate-ca-certificates) (see [Managing Intermediate Certificates](intermediates)).
4. **Root Store Policy Review:** Review the specific inclusion requirements for each target program on [Useful Resources: Root Store Information](../resources#root-store-information).

---

## 2. Creating a Root Inclusion Request Case

1. [Log in to the CCADB](https://ccadb.my.site.com/CustomLogin) (see [Getting Started](getting-started) if needed).
2. Click the **My CA** tab in the top navigation bar.
3. Click the **CASES** sub-tab under your CA Owner's name near the upper-left corner.
4. Click the **New** button on the right side of the page (below **Get URLs**).
5. Select **Root Inclusion Request** and click **Next**.
6. Enter a clear, descriptive **Subject** for your case, for example:
   - `Include <Root Name> Root Certificate in Multiple Root Stores`
   - `Include <Root 1> and <Root 2> Certificates in <Root Store>`
7. Click **Save**.
8. Open your newly created case using any of the following methods:
   - Click the case number in the green confirmation banner across the top of the page (`Case ###### was created`).
   - Return to **My CA** → **CASES** and click the case number in the top row of the **Case** column.
   - Go to your CCADB **Home** page, expand **Open Cases** under **CA Task List**, and click the case number.

When the case opens, the leftmost **INSTRUCTIONS** tab displays a brief checklist of the workflow. Across all tabs, click the question mark icon (**`?`**) to the right of any field for inline guidance on the expected input.

---

## 3. Selecting Root Certificates and Root Store Programs

You can apply to one or multiple Root Store Programs within a single `Root Inclusion Request` case:

1. Click any Root Store Program tab (**Apple**, **Google Chrome**, **Microsoft**, or **Mozilla**).
2. Click the **Add/Select Root Certificates** button at the top of the tab.
3. In the **Add/Select Root Certificates for this Case** window, click **Select Root Certificates** to view your CA Owner's root certificates.
4. In the **Root Store Applying To** column on the left, check the box next to each Root Store Program (`Apple`, `Google Chrome`, `Microsoft`, `Mozilla`) to which you are requesting inclusion for each applicable root certificate.
5. Click **Save**, then click **Go Back** to return to the case.

> **Why Are Some Root Certificate Checkboxes Grayed Out?**
> If a root certificate row appears shaded with italicized text and disabled **Root Store Applying To** checkboxes, its **PKI Hierarchy** section has not yet been fully populated on the root certificate record. Create an [Add/Update Root Request](updates) case, complete all required fields on the [ROOT INFORMATION](updates#root-information) tab, and wait for a Root Store Operator to process and sync that case before selecting the root here.

### How Selected Roots Appear (`Root Case` Records)
Once selected, each root certificate appears on the applicable Root Store Program tab(s) inside its own collapsible **Root Case** subsection labeled `[R########] <Root Certificate Name>` beneath the main `Case Number [########]` section.

To change your root or program selections before submitting:
- Click **Add/Select Root Certificates** → **Select Root Certificates** to add another root certificate or apply to an additional Root Store Program (displays all root certificates under your CA Owner).
- Click **Add/Select Root Certificates** → **Deselect Root Certificates** to remove a root certificate or Root Store selection from the case (displays only the root certificates currently selected in the case).

---

## 4. Completing Root Store Program Tabs

Each selected Root Store Program tab is organized into two levels:
1. **Case-Level Section (`Case Number [########]`):** Program-wide disclosures (such as Value Statements) along with read-only fields showing that Root Store Operator's overall request status and notes.
2. **Per-Root Subsections (`[R########] <Root Name>`):** Certificate-specific inclusion fields along with read-only fields for that root's individual inclusion status, applied constraints, and operator notes.

Click the **pencil icon** next to any editable field to enter data (you can also use **Show Changes** or **Print View** at the top of a tab to review your entries). At a minimum, you must populate every subsection displaying a **yellow warning message**, though you should complete as many applicable fields as possible. If required fields are missing—including newly added required fields on a pre-existing `Root Case` record—CCADB displays a warning when you click **Submit to Root Store**.

### Shared Per-Root Fields
Fields marked with the **3-node data-model icon** (next to **`?`**) are shared across all Root Store Program tabs. **You only need to enter these values once** on any selected Root Store tab, and CCADB automatically populates them across the other selected tabs for that root certificate:

- **`Does the CA Owner operate this CA?` / `CA Owner Operating?`:** Select `Yes` if the CA Owner associated with this root certificate in the CCADB maintains sole control of its private key material and operates the infrastructure in which the root resides; otherwise select `No`.
- **`Revocation Tested`:** Test your hierarchy's test websites using [certificate.revocationcheck.com](https://certificate.revocationcheck.com/) to verify there are no revocation errors, and paste the test results/URL.
- **`CA/Browser Forum Lint Test`:** Run the [CCADB CA Checker / Lint Test](https://cachecker-dot-ccadb-231121.appspot.com/) to verify there are no certificate profile lint errors, and paste the summary URL/results.
- **`EV Tested`:** If Extended Validation (EV) TLS treatment is requested for the root hierarchy, run the [EV Readiness Test](https://evready-dot-ccadb-231121.appspot.com/evready) to verify there are no errors, and paste the results.

---

### Apple
Complete the fields below in accordance with the [Apple Root Certificate Program Policy](https://github.com/apple/apple-root-program/blob/main/policy.md).

#### Case-Level Fields (`Case Number [########]`)
Provide direct links to externally hosted documents for the first four fields, plus `Yes`/`No` responses for ACME support:

- **`Values & Benefits Statement`:** Link to an externally hosted document explaining the added value and benefits your CA provides to the industry, Apple, and users of Apple software and hardware, addressing:
  - *Incident Reporting:* Your process for timely, transparent compliance incident reporting; measures demonstrating transparency; root cause analysis methodology ensuring complete identification of all root causes; and how incident details and root causes are mapped to effective remediation tasks.
  - *Audits & Policy Maintenance:* How internal processes reflect relevant PKI industry standards for annual audits and policy maintenance, how those standards are implemented, and any participation in Standards Development Organizations (SDOs).
  - *CA/B Forum:* Involvement in the CA/Browser Forum, examples of contributions to the Web PKI, and future goals aligned with the CA community.
  - *Privacy & Security:* Your organization's consumer privacy policy and security policies protecting personal data from third parties.
- **`CA Lifecycle Management`:** Link to an externally hosted document describing how your CA regularly replaces root CA certificates and key material under current best practices, addressing:
  - Process, criteria, and timelines for replacing root CA certificates and keys (including keys generated under superseded security standards).
  - Whether and how cross-certification is performed between generations.
  - Root CA certificates currently operated and any additional roots in active planning.
  - How far before expiration replacement roots are signed, when new roots are submitted to the Apple Root Program (ARP), and how quickly subscribers transition between roots.
  - Criteria required before deprecated root CA certificates can be removed from the ARP.
  - Approach to cryptographic algorithm agility and addressing potential key-size weaknesses.
- **`Linting`:** Link to an externally hosted document detailing technical certificate profile compliance controls, addressing:
  - *Pre-issuance Linting:* Pre-issuance linting processes (or implementation plans), tools/software used, assurance of standards adherence, updates, integration with issuance pipelines, error reporting, testing/validation, and community contributions.
  - *Post-issuance Linting:* Post-issuance linting processes, coverage/timelines, tools used, and procedures for responding to any detected lint findings.
  - *Linting Tools:* Linters operated, how linters and configurations are updated, assessment criteria and circumstances under which lints may be disabled, and processes for reviewing and contributing new lints.
- **`Customer and Change Management`:** Link to an externally hosted document describing how your CA manages ecosystem and policy changes, addressing:
  - Public resources provided for upcoming changes in industry standards, policies, and requirements, and mechanisms used to communicate those changes to subscribers.
  - How current and accurate subscriber contact information is maintained.
  - Process for collecting feedback on potential Web PKI changes and their ecosystem impact.
- **`ACME Domain Validation`:** Select `Yes` or `No` to indicate whether you support domain validation compliant with the ACME protocol.
- **`ACME Certificate Issuance`:** Select `Yes` or `No` to indicate whether you support certificate issuance via the ACME protocol.

#### Per-Root Fields (`[R########]`)
- **`Replacing a Certificate?`**, **`SHA-256 Hash of the Cert being Replaced`**, and **`Certificate Replacement Date`:** Check the box if this root replaces a root currently in the Apple Root Program, and provide the replaced root's SHA-256 hash and past or planned replacement date.
- **`Apple Trust Bits`:** Select the requested certificate purposes (`serverAuth`, `clientAuth`, `emailProtection`, `timeStamping`, `codeSigning`, `BrandIndicatorforMessageIdentification`), ensuring the selected combination is permitted under Section 2.1.3 of the Apple Root Certificate Program Policy.
- **`Apple EV TLS Enabled`** and **`Apple EV TLS Policy OID(s)`:** Check the box if planning to issue EV TLS certificates under this root, and enter `2.23.140.1.1` along with your CA's EV TLS policy OID(s) required by EV Guidelines Section 7.1.4.3, Item 2.
- **[Shared Per-Root Fields](#shared-per-root-fields):** `CA Owner Operating?`, `Revocation Tested`, `CA/Browser Forum Lint Test`, and (if applicable) `EV Tested`.

---

### Google Chrome
Complete the per-root fields below in accordance with the [Chrome Root Program Policy](https://g.co/chrome/root-policy).

#### Per-Root Fields (`[R########]`)
- **`Replacing an existing Cert in CRS?`:** Select if this root will replace an existing certificate in the Chrome Root Store, and provide the replaced certificate's SHA-256 hash and expected replacement date.
- **`Understanding Value&Risk Form Completed?`:** Select `Yes` once you have completed the Chrome Root Program Risk & Value form.
- **`EV Treatment Requested?`:** Select if EV treatment is requested for the hierarchy under this root certificate.
- **[Shared Per-Root Fields](#shared-per-root-fields):** `Does the CA Owner operate this CA?`, `Revocation Tested`, `CA/Browser Forum Lint Test`, and (if applicable) `EV Tested`.

---

### Microsoft
Complete the fields below in accordance with the [Microsoft Trusted Root Program Requirements](https://aka.ms/RootCert).

#### Case-Level Fields (`Case Number [########]`)
- **`Value Statement`:** Provide a detailed statement explaining why inclusion of the root certificate(s) is necessary and what value it brings to Microsoft users and the broader security ecosystem (see [Microsoft Trusted Root Program Requirements](https://aka.ms/RootCert) for guidance).
- **`Additional Info for Microsoft`:** Provide any supplemental context relevant to your Microsoft application.

#### Per-Root Fields (`[R########]`)
- **`Purpose of the Root`:** Provide a concise statement explaining why this specific root should be included in the program.
- **`Friendly Name`:** Optionally provide a user-defined friendly name for the root certificate.
- **`Replacing an existing Cert in TRP?`**, **`SHA-256 Hash of the Cert being Replaced`**, and **`Certificate Replacement Date`:** Select if replacing an existing root in the Microsoft Trusted Root Program, and enter the replaced root's SHA-256 hash and replacement date.
- **`Are you a Qualified TSP?`:** Select `Yes` if the CA Owner is a Qualified Trust Service Provider (qTSP) under EU regulations; otherwise select `No`.
- **`Microsoft EV TLS Enabled`** and **`Microsoft EV TLS Policy OID(s)`:** Check if planning to issue EV TLS certificates, and enter your CA-specific EV policy OID(s) required by EV Guidelines Section 7.1.4.3, Item 2 (`2.23.140.1.1` is added automatically).
- **`Microsoft TLD Restriction`:** Specify any applicable top-level domain (TLD) restriction.
- **[Shared Per-Root Fields](#shared-per-root-fields):** `Does the CA Owner operate this CA?`, `Revocation Tested`, `CA/Browser Forum Lint Test`, and (if applicable) `EV Tested`.

---

### Mozilla
Complete the fields below in accordance with the [Mozilla Root Store Policy](https://www.mozilla.org/en-US/about/governance/policies/security-group/certs/policy/).

#### Case-Level Fields (`Case Number [########]`)
- **`Value Statement (Link)`:** Provide a direct URL to your CA's value statement prepared according to Mozilla's [Quantifying Value](https://wiki.mozilla.org/CA/Quantifying_Value) guidance.
- **`Bugzilla Bug (Link)`:** Provide the URL of the Mozilla Bugzilla bug filed for your root inclusion request.

#### Per-Root Fields (`[R########]`)
- **`Mozilla Trust Bits`:** Select `Websites`, `Email`, or both, and click the arrow to move them to **Chosen**.
- **`Mozilla EV Policy OID`:** If planning to issue EV TLS certificates under this root, enter **only** the CA/Browser Forum EV policy OID `2.23.140.1.1`.
- **`Mozilla Applied Constraints`:** Indicate whether the root CA will be constrained by Mozilla to any top-level (gTLD/ccTLD) or second-level domains.
- **[Shared Per-Root Fields](#shared-per-root-fields):** `Does the CA Owner operate this CA?`, `Revocation Tested`, `CA/Browser Forum Lint Test`, and (if applicable) `EV Tested`.

---

## 5. Submitting and Tracking Your Request (`CASE PROGRESS`)

### Submitting to Root Store Operators
Once all required sections across your selected Root Store Program tabs are complete, click the **Submit to Root Store** button in the upper-right corner of the case page.

### Tracking Status on `CASE PROGRESS`
The **CASE PROGRESS** tab displays a consolidated view of your inclusion request across all selected Root Store Programs. Because each Root Store Operator evaluates requests on its own timeline, CCADB tracks both an **overall case status** (in the top highlight panel) and an **independent Case-level request status** for each selected Root Store Program:

| Case Stage / Trigger | Overall `Case Request Status` (Highlight Panel) | Selected Program Statuses (Case Level) |
|---|---|---|
| **Case created** *(automatic)* | `Initial Request Created` | `Not Applicable` |
| **Root certificate(s) selected** *(automatic)* | `CA Providing Data` | `CA Providing Data` |
| **CA clicks `Submit to Root Store`** *(automatic)* | `Verification By Root Store` | `Request Submitted` |
| **Root Store Operator evaluation** *(set per program)* | `Verification By Root Store` | Set independently by each Root Store Operator (see table below) |
| **All selected evaluations finished** | `Complete` or `Closed` | Retains each Root Store Operator's selected final status |

During and after evaluation, each Root Store Operator sets its Case-level status to one of the following program-specific values:

| Root Store Program | Operator Request Status Values |
|---|---|
| **Apple** | `In Process`, `Ready`, `Approved`, `On Hold`, `Withdrawn`, `Denied` |
| **Google Chrome** | `In Process`, `Approved`, `On Hold`, `Withdrawn`, `Denied` |
| **Microsoft** | `In Process`, `Approved`, `On Hold`, `Withdrawn`, `Denied` |
| **Mozilla** | `In Process`, `Pending Approval`, `Approved, Pending Inclusion`, `Approved, Pending Inclusion and EV`, `Included, Pending EV`, `On Hold`, `Withdrawn`, `Denied`, `Complete` |

### Case Comments and Public Discussion
- **Shared Case Comments (`Add Comment`):** Clicking **Add Comment** on the **CASE PROGRESS** tab posts a comment visible to **all** Root Store Programs selected on the case. 
- **Public Discussion (`public@ccadb.org`):** For Root Store Programs that require public discussion, a Root Store Operator will initiate a shared six-week discussion period in the `public@ccadb.org` group once prerequisites are verified and a discussion slot opens (at most three concurrent inclusion discussions run at a time, with root replacement requests prioritized). CA Owners are expected to monitor `public@ccadb.org` and respond promptly to all questions—see [Root Inclusion Public Discussion](public-group#root-inclusion-public-discussion) for full details.
