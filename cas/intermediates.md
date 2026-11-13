# Managing Intermediate Certificates

CA Owners can view root and intermediate certificate records across the CCADB, and can **directly add and edit** intermediate certificate records that chain up to root certificates they own without opening a review case.

> **Note:** The CCADB considers the terms **intermediate** and **subordinate** synonymous. To add or update CA Owner or root certificate records (which require Root Store Operator case review), see [Managing CA Owner and Root Certificate Records](updates).

## Disclosure Scope

Per [CCADB Policy Section 3.2](../policy#32-subordinate-ca-certificates), CA Owners must maintain accurate records for all subordinate CA certificates capable of validating to a certificate included in a Root Store or associated with a [Root Inclusion Request](inclusion).

## Table of Contents

1. [Adding Intermediate Certificate Data](#adding-intermediate-certificate-data)
   - [Cloning an Existing Intermediate Record](#clone)
2. [Updating Audit and Policy Information](#updating-audit-statements)
   - [Mass Update of Audit/Non-Audit Info](#mass-update-of-audit-non-audit-info)
3. [Marking an Intermediate Certificate as Revoked](#marking-an-intermediate-certificate-as-revoked)
4. [Automating Updates via the CCADB API](#api)

---

<a id="adding-intermediate-certificate-data"></a>
## 1. Adding Intermediate Certificate Data

1. [Log in to the CCADB](https://ccadb.my.site.com/CustomLogin) (see [Getting Started](getting-started) if needed).
2. Locate and open the **issuing (parent)** root or intermediate certificate record that signed the new intermediate certificate using either method:
   - Click the **My CA** tab, then click the **CA HIERARCHY** sub-tab under your CA Owner's name in the upper-left corner.
   - Click the **magnifying glass** search icon in the upper-right corner, enter the SHA-1 or SHA-256 fingerprint of the parent certificate, and press **Return**.
3. Click the **New Intermediate Cert** button near the upper-right corner of the parent certificate page.
4. Paste the intermediate certificate's [PEM data](fields#pem-data) (`-----BEGIN CERTIFICATE-----` to `-----END CERTIFICATE-----`) into the dialog window, ensuring there are no extra characters, headers, or blank lines.
5. Click **Validate PEM Info** to parse and verify the certificate:
   - If validation succeeds, click **Update Intermediate Cert**.
   - If validation fails, click **Cancel**, verify the [PEM formatting](fields#pem-data), and try again. If valid PEM data continues to fail, email `support [at] ccadb [dot] org` with the PEM attached.
6. On the newly created intermediate certificate record, verify the parsed values in the **Certificate Data** section. (If you ever need to re-upload the PEM, open the **`▼`** button overflow menu in the upper-right corner and select **Add/Update PEM Info**.)
7. Click **Edit**, populate all required disclosure sections (see [CCADB Field Reference and Valid Values](fields)), and click **Save**:
   - **Subordinate CA Owner:** Populate `Subordinate CA Owner` with the exact organization name from the subordinate CA's audit statements, unless *both* private key control and domain/IP validation are performed by the organization listed in the parent certificate's audit statement ([Field Reference](fields#certificate-ownership-and-hierarchy-fields)).
   - **[Audit Information](fields#audit-information):** If the intermediate certificate is covered by the issuing parent certificate's current (or next periodic) audit statements, check `Audits Same as Parent`. Otherwise, leave it unchecked, enter the subordinate-specific audit URLs and dates, save, and click `Audit Letter Validation [ALV]`.
   - **[Non-Audit Information](fields#non-audit-information):** If the intermediate certificate uses the exact same policy and self-assessment documents as its issuing parent (or a subset), check the applicable **`* Same as Parent`** boxes (`CP Same as Parent` and `CPS Same as Parent`, `CP/CPS Same as Parent`, `MD/AsciiDoc CP/CPS Same as Parent`, and `Self-Assessment Same as Parent`). Otherwise, enter the subordinate-specific document URLs and Effective Dates.
   - **[CRL Disclosures](fields#pertaining-to-certificates-issued-by-this-ca):** If the intermediate CA has **not yet issued any certificates**, enter `[""]` into `JSON Array of Partitioned CRLs`. Once issuance begins, update `JSON Array of All Full CRL URLs` or `JSON Array of Partitioned CRLs` within 7 days of first issuance (or within 4 hours of first revocation).
   - **[Policy Identifiers and Automation](fields#issuance-policy-identifier-and-automation-fields):** Select applicable `CA/B Forum Certificate Policy Identifier` values and populate `ACME Directory URL(s)`, `Other Automated Solution Description`, and `Automation Test Certificate Website` where applicable.

<a id="clone"></a>
### Cloning an Existing Intermediate Record

If you are adding multiple intermediate certificates that share the same CP/CPS and audit statements, you can use the **Clone** button to avoid re-entering those sections:

1. Create and save one intermediate certificate record following Steps 1 through 7 above, confirming its **Audit Information** and **Non-Audit Information** sections (or `* Same as Parent` checkboxes) are complete.
2. Click the **Clone** button on that record. CCADB creates a new intermediate certificate record copying the `Parent CA Owner/Certificate` field, **Audit Information**, and **Non-Audit Information**.
3. On the cloned record, click **Add/Update PEM Info** (in the upper-right button bar or **`▼`** overflow menu) and paste the new intermediate certificate's [PEM data](fields#pem-data).
4. Click **Validate PEM Info**, then click **Update Intermediate Cert** to populate the parsed certificate fields.
5. Verify (and update via **Edit** → **Save**, if different) the `Parent CA Owner/Certificate`, `Subordinate CA Owner`, CRL URLs, and Policy Identifier / Automation fields for the new certificate.

---

<a id="updating-audit-statements"></a>
## 2. Updating Audit and Policy Information

While root certificate audits and policy documents are submitted via an [Add/Update Root Request](updates) case, CA Owners directly update intermediate certificate records whenever new annual audit statements, policy documents, or self-assessments are published (within 14 calendar days of policy effective dates and within 92 calendar days of audit period end dates).

> **Important:** Whenever an intermediate certificate shares the same audit statements or policy documents as the parent certificate that signed it, check **`Audits Same as Parent`** and the applicable **`* Same as Parent`** policy checkboxes rather than duplicating URLs across child records. Note that checking `Audits Same as Parent` still requires the intermediate certificate's SHA-256 fingerprint to be explicitly listed in scope in the parent certificate's audit statement ([CCADB Policy Section 5](../policy#5-audit-disclosures)).

1. [Log in to the CCADB](https://ccadb.my.site.com/CustomLogin).
2. Navigate to the intermediate certificate record using any of the following methods:
   - On your CCADB **Home** page under **CA Task List**, open **Intermediate Certificates with Outdated Audit Statements**, **Intermediate Certificates with Missing Information**, or **Intermediate Certificates with Failed ALV Results**, and click the certificate link.
   - Click **My CA** → **CA HIERARCHY** and select the intermediate certificate.
   - Click the **magnifying glass** search icon in the upper-right corner and search by SHA-1 or SHA-256 fingerprint.
3. Click **Edit**, update the [Audit Information](fields#audit-information) and/or [Non-Audit Information](fields#non-audit-information) fields, and click **Save**.
4. If you entered or updated audit statement URLs directly on the intermediate record (i.e., `Audits Same as Parent` is unchecked), click the `Audit Letter Validation [ALV]` button to validate the audit letters and confirm there are no [ALV errors](ALV#intermediate-certificates).
5. *(Optional)* If sibling intermediate certificates under the same parent need the exact same Audit or Non-Audit updates, use **Mass Update Audit/Non-Audit Info** below.

<a id="mass-update-of-audit-non-audit-info"></a>
### Mass Update of Audit/Non-Audit Info

The **Mass Update Audit/Non-Audit Info** button copies Audit and Non-Audit values from one intermediate certificate (**Source**) to other intermediate certificates signed by the **same parent certificate** (**Targets**):

1. Open the updated intermediate certificate record you want to use as the **Source** and click **Mass Update Audit/Non-Audit Info**.
2. CCADB checks all sibling intermediate certificates signed by the same parent certificate and displays a side-by-side comparison whenever a **Target** certificate has different Audit or Non-Audit values (differences are highlighted in **blue text**).
3. Click **Yes** in each section you want to overwrite on the Target certificate so it matches the Source, or click **Next Target Cert** to skip to the next sibling certificate.
4. Click **Exit** at any time to pause; re-clicking **Mass Update Audit/Non-Audit Info** later automatically skips sibling certificates that already match the Source.

---

<a id="marking-an-intermediate-certificate-as-revoked"></a>
## 3. Marking an Intermediate Certificate as Revoked

Per [CCADB Policy Section 3.2](../policy#32-subordinate-ca-certificates), revoked subordinate CA certificates must be marked as `Revoked` in the CCADB **within 7 calendar days of revocation** (if the certificate is not yet in the CCADB, [add the intermediate certificate record](#adding-intermediate-certificate-data) first, then mark it as revoked):

1. Open the intermediate certificate record in the CCADB and click **Edit**.
2. Set `Revocation Status` to `Revoked`.
3. Enter `Date of Revocation`, matching the exact revocation date in the issuing CA's CRL.
4. Select `RFC 5280 Revocation Reason Code`, matching the `reasonCode` extension published in the issuing CA's CRL (every CRL entry for a revoked subordinate CA certificate must include a `reasonCode` extension).
5. Click **Save**.

> **Post-Revocation Requirements:**
> - **Security-Related Revocations:** If a subordinate CA certificate is revoked due to a security concern, the CA Owner must also file a confidential [Incident Report](incident-report#how-do-i-submit-a-security-sensitive-incident-report) in Bugzilla.
> - **Audit Coverage After Revocation:** Although revoked records no longer require ongoing CRL or policy URL updates in CCADB, the revoked subordinate CA certificate **must still appear in scope on at least one periodic audit statement** following revocation ([CCADB Policy Section 5.1](../policy#51-scope-of-certificates-covered-by-an-audit)).

---

<a id="api"></a>
## 4. Automating Updates via the CCADB API

CA Owners with root certificates included in one or more CCADB Root Stores may automate retrieving and updating intermediate certificate records using the [CCADB Intermediate Certificate APIs](https://github.com/mozilla/CCADB-Tools/tree/master/API_AddUpdateIntermediateCert):

- **`GetCertificateIdAPI`:** Returns the CCADB Salesforce record ID for a root or intermediate certificate.
- **`AddUpdateIntermediateCertAPI`:** Adds a new intermediate certificate record or updates an existing intermediate certificate record in the CCADB.

### API Access and Usage Rules
- **Requesting Access:** Request API credentials or sandbox accounts by filing a ticket in the Mozilla Bugzilla [Common CA Database component](https://bugzilla.mozilla.org/enter_bug.cgi?product=CA%20Program&component=Common%20CA%20Database) or contacting support [at] ccadb [dot] org.
- **Account & License Limits:** Production API access is limited to **one API account per CA Owner**, and authenticating to the production API counts toward your organization's [daily-unique-login allotment](usage-guidelines#api-credentials).
- **Mandatory Sandbox Testing:** All API integration development and testing must be performed in the **CCADB Sandbox** environment rather than production (see [CCADB Usage Guidelines](usage-guidelines#sandbox-environment-accounts)).
