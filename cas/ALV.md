# Audit Letter Validation (ALV)

The CCADB uses an Audit Letter Validation (ALV) tool provided by Microsoft to automatically parse and validate audit statements. ALV eliminates manual processing, which requires audit statements to follow specific content and formatting rules to function properly. If an audit statement fails to meet any of the [Audit Statement Content](../policy#52-audit-statement-content) or [ALV Formatting](../policy#523-alv-formatting) requirements, the CA Owner must work with their auditor to provide an audit statement that passes ALV.

## Table of Contents

1. [Root Certificates](#root-certificates)
2. [Intermediate Certificates](#intermediate-certificates)
3. [Testing Audit Statements with ALV](#testing-audit-statements-with-alv)
4. [Common ALV Findings](#common-alv-findings)

---

## Root Certificates

CA Owners are required to update the audit, policy document, [self-assessment](self-assessment), and test website information for their certificate hierarchies at least annually. To provide audit statements for root certificates, create an [Add/Update Root Request](updates#audits) case in the CCADB for each distinct set of audits (including **Standard Audit**, **NetSec Audit**, **TLS BR Audit**, **TLS EVG Audit**, **Code Signing Audit**, **S/MIME BR Audit**, and **VMC Audit**, as applicable).

* [Managing CA Owner and Root Certificate Records (Add/Update Root Request)](updates)

---

## Intermediate Certificates

Subordinate CA Owners who operate non-technically-constrained intermediate certificates have the same technical issuance capability as CA Owners with root certificates directly included in a Root Store. Because such subordinate CA Owners can issue certificates for any website or domain, the same compliance and audit rules apply to all subordinate CA Owners operating non-technically-constrained intermediate certificates.

> **Note:** The CCADB considers the terms **intermediate** and **subordinate** synonymous.

To enforce compliance across the certificate hierarchy, [CCADB Policy Section 3.2](../policy#32-subordinate-ca-certificates) requires disclosure of subordinate CA certificates capable of validating to an included root certificate or a root associated with a [Root Inclusion Request](inclusion). The CCADB automatically runs ALV on intermediate certificate records and surfaces results to CA Owners and Root Store Operators on their CCADB **Home** pages.

CA Owners must annually update audit and policy documents for non-technically-constrained intermediate certificates chaining to root certificates included in a Root Store. To provide this information for intermediate certificates, directly [update the corresponding intermediate certificate record](intermediates#updating-audit-statements) in the CCADB and click the **Audit Letter Validation [ALV]** button.

When the audit statements for an intermediate certificate are the same as the parent certificate that signed it, check the `Audits Same as Parent` checkbox instead of duplicating audit URLs on the child record. When `Audits Same as Parent` is checked, the CCADB traverses up the parent chain until audit statements are found and runs ALV against those parent audit statements. When `Audits Same as Parent` is unchecked, the CCADB passes the audit statements entered directly on the intermediate certificate record into ALV.

### Intermediate ALV Result Fields

Clicking **Audit Letter Validation [ALV]** on an intermediate certificate record (or waiting for CCADB's automated background checks) populates the following fields:

* **`Standard Audit ALV Found Cert`:** Set to `PASS` when ALV finds the certificate's SHA-256 fingerprint in the Standard Audit statement.
* **`NetSec Audit ALV Found Cert`:** Set to `PASS` when ALV finds the certificate's SHA-256 fingerprint in the NetSec Audit statement.
* **`TLS BR Audit ALV Found Cert`:** Evaluated only when [Derived Trust Bits](fields#system-generated-fields) includes `Server Authentication`; set to `PASS` when ALV finds the certificate's SHA-256 fingerprint in the TLS BR Audit statement.
* **`TLS EVG Audit ALV Found Cert`:** Evaluated only when [Derived Trust Bits](fields#system-generated-fields) includes `Server Authentication` and [EV SSL Capable](fields#system-generated-fields) is `TRUE`; set to `PASS` when ALV finds the certificate's SHA-256 fingerprint in the TLS EVG Audit statement.
* **`Code Signing Audit ALV Found Cert`:** Evaluated only when [Derived Trust Bits](fields#system-generated-fields) includes `Code Signing`; set to `PASS` when ALV finds the certificate's SHA-256 fingerprint in the Code Signing Audit statement.
* **`S/MIME BR Audit ALV Found Cert`:** Evaluated only when [Derived Trust Bits](fields#system-generated-fields) includes `Secure Email`; set to `PASS` when ALV finds the certificate's SHA-256 fingerprint in the S/MIME BR Audit statement.

### Resolving `FAIL` Results on Intermediate Records

When ALV returns `FAIL` for `Standard Audit ALV Found Cert`, `NetSec Audit ALV Found Cert`, `TLS BR Audit ALV Found Cert`, `EVG BR Audit ALV Found Cert`, `Code Signing Audit ALV Found Cert`, or `S/MIME Audit ALV Found Cert` on one of your intermediate certificate records:

1. Check the corresponding audit statement to confirm whether the certificate's SHA-256 fingerprint is listed in scope.
2. If the SHA-256 fingerprint is listed, verify that it meets the [ALV formatting specifications](../policy#523-alv-formatting) (uppercase hex, text-searchable PDF, no colons, no spaces, and no line feeds). If not, have your auditor provide an updated audit statement that meets the [formatting requirements](../policy#523-alv-formatting).
3. If the SHA-256 fingerprint is listed and formatted properly and you believe ALV produced a false negative, explain the discrepancy in the corresponding `...ALV Comments` field (`Standard Audit ALV Comments`, `NetSec Audit ALV Comments`, `TLS BR Audit ALV Comments`, `EVG BR Audit ALV Comments`, `Code Signing Audit ALV Comments`, or `S/MIME Audit ALV Comments`).
4. If the audit statement is genuinely missing the SHA-256 fingerprint for the certificate, file a public [Incident Report](incident-report) in Bugzilla and paste the link to the Incident Report into the applicable `...ALV Comments` field.

**Important Audit Scope Rules ([CCADB Policy Section 5.1](../policy#51-scope-of-certificates-covered-by-an-audit)):**

* **Newly Issued Intermediate Certificates:** If the CA Owner holds a currently valid audit report when a new intermediate certificate is created, the current audit statement does not need to be reissued immediately; the new certificate must appear in scope on the CA Owner's next periodic audit statements.
* **Capability Determines Audit Scope:** Intermediate certificates containing `Server Authentication` in [Derived Trust Bits](fields#system-generated-fields) are technically capable of issuing TLS certificates and must be listed in the corresponding TLS BR Audit statement regardless of whether they actively issue TLS certificates.
* **Duplicate `Subject + SPKI` Intermediate Certificates:** If multiple intermediate certificates share the same Subject and Subject Public Key Info (SPKI), **every** distinct certificate's SHA-256 fingerprint must be listed in the applicable audit statements according to its [Derived Trust Bits](fields#system-generated-fields).
* **Cross-Certificates:** Cross-certificates are treated as intermediate certificates and must be disclosed and explicitly listed by SHA-256 fingerprint in all applicable audit statements of the issuing CA Owner according to [Derived Trust Bits](fields#system-generated-fields).
* **Self-Signed Certificates Sharing `Subject + SPKI` with an Included Root:** Self-signed certificates that share a Subject + SPKI with a root certificate that is (or was) included in a Root Store are treated as subordinate CA certificates because a valid chain can be constructed (`leaf -> older/newer root -> included root`). Their SHA-256 fingerprints must also be listed in the applicable audit statements according to [Derived Trust Bits](fields#system-generated-fields).

**Acceptable Remediation for Missing Fingerprints:**

* **Obtain a Revised Audit Report:** Have your auditor issue a revised audit statement that includes the intermediate certificate's SHA-256 fingerprint (see [Audit Statement Date rules for revised reports](fields#audit-information)).
  * If the certificate existed during past audit periods without being listed, you must also file an [Incident Report](incident-report).
  * An Incident Report may not be required if the omitted certificate is self-signed and shares the same Subject + SPKI as another root certificate already listed in the audit statement.
* **Revoke the Intermediate Certificate:** Revoke the intermediate certificate in accordance with applicable Root Store policies and CA/Browser Forum Baseline Requirements, and [mark the record as Revoked](intermediates#marking-an-intermediate-certificate-as-revoked) in the CCADB.
  * Failing to complete revocation within the timeline required by Section 4.9 of the Baseline Requirements constitutes a separate compliance violation requiring its own [Incident Report](incident-report#how-are-reports-scoped).

---

## Testing Audit Statements with ALV

CA Owners are encouraged to coordinate with their auditors and test preliminary audit statements with ALV before final sign-off to confirm all formatting and fingerprint checks pass:

1. **Upload the Preliminary PDF(s) to a Temporary HTTPS URL:** Use any of the following options:
   * **Bugzilla Attachment:** Attach the preliminary PDF to your CA's `CA Documents` bug in Bugzilla (see [Uploading Documents](fields#uploading-documents)) and copy the direct attachment URL (e.g., `https://bugzilla.mozilla.org/attachment.cgi?id=...`).
   * **Auditor or CA Website:** Host the preliminary PDF at a temporary `https://` URL on the audit firm's or CA Owner's website.
   * **Google Drive:** Share the PDF with *"Anyone with the link"* and format the URL for direct download: `https://drive.google.com/uc?export=download&id=<FILE_ID>`.
2. **Create or Open an Add/Update Root Request Case:** Follow [Creating an Add/Update Root Request Case](updates#1-creating-an-addupdate-root-request-case) and open the **AUDITS** tab.
3. **Enter Auditor and Preliminary Audit Details:**
   * Populate the **Audit Firm** section per [Auditor Information](fields#auditor-information).
   * Populate each applicable section (`Standard`, `NetSec`, `TLS BR`, etc.) per [Audit Information](fields#audit-information), pasting the temporary HTTPS URL into `Audit Statement (Link)` and selecting the **Applicable root certificates**.
4. **Flag the Case as Preliminary Testing:** On the **CASE PROGRESS** tab, click **Add Comment** and enter `"Preliminary Audit Reports"` so Root Store Operators know you are only testing preliminary files (do **not** click **Submit to Root Store** yet).
5. **Run ALV:** Return to the **AUDITS** tab and click **Validate Audits [ALV]** (if testing only a subset of expected audits for a root, click **Proceed Anyways** when prompted). After the results window appears, click **Go Back** and expand **ALV Results Summary** at the bottom of the tab:
   * Ignore `Audit Letter Not Found In Certified Location` if testing via Bugzilla, Google Drive, or an uncertified temporary host (Bugzilla and Google Drive are not accepted as trusted locations for final WebTrust/ETSI reports when standard CPA Canada or CAB hosting applies).
   * Work with your auditor to resolve any other errors using [Common ALV Findings](#common-alv-findings). For issues not covered below, contact `support [at] ccadb [dot] org`.
6. **Replace with Final Audit Statements:** Once all errors are resolved and final signed reports are published:
   * Remove any temporary preliminary files from public test locations.
   * Update `Audit Statement (Link)` in the existing **Add/Update Root Request** case with the final production URLs (or WebTrust Seal URLs) and click **Validate Audits [ALV]** again.
   * Add a comment on the **CASE PROGRESS** tab stating `"Final Audit Reports"`, then click **Submit to Root Store**.

> **Note:** The steps above apply to testing root certificate audit statements in a CCADB Case. To validate audit statements entered directly on an intermediate certificate record, see [Managing Intermediate Certificates: Updating Audit and Policy Information](intermediates#updating-audit-statements).

---

## Common ALV Findings

ALV formatting specifications for SHA-256 fingerprints and dates are defined in [Section 5.2.3 of the CCADB Policy](../policy#523-alv-formatting).

| ALV Error | Meaning | Recommended Action |
|---|---|---|
| `Thumbprint not found` | The SHA-256 fingerprint of the certificate was not found in the audit statement. | • Verify that the certificate's SHA-256 fingerprint is explicitly listed in the audit statement and follows [Section 5.2.3 formatting rules](../policy#523-alv-formatting) (uppercase hex, no colons, no spaces, and no line feeds).<br>• Request an updated audit statement from your auditor listing the properly formatted SHA-256 fingerprints of every in-scope root and intermediate certificate. |
| `Statement Date Not Found` | The audit statement issuance date was not found in the audit statement. | • Check that the date the audit statement was signed/issued is clearly stated and follows accepted [date formats](../policy#523-alv-formatting).<br>• Request an updated audit statement from your auditor if needed.<br>• If the date is properly formatted and ALV raised a false alert, add an explanatory note in the Case Comment or `...ALV Comments` field. |
| `Audit Period Not Found` | ALV could not parse the audit period start and end dates in the audit statement. | • Confirm the audit period dates match an accepted `<date> <splitter> <date>` format (`May 7, 2025 to May 6, 2026`, `2025-05-07 - 2026-05-06`, etc.) with no ordinal suffixes like `"7th"`.<br>• Place the audit period near the top of the document on a single contiguous line rather than split across separate table rows.<br>• Note that point-in-time readiness audits (or periods shorter than one month) trigger this message and are reviewed manually by Root Store Operators. |
| `Failed to validate EKU ... because the standard names and standard policies are not found in the audit letters` | ALV could not locate the expected audit criteria text (case-insensitive) for an applicable EKU (for example, `319 411-1 v1.1.1, dvcp;ovcp;ptc-br`). | Confirm that the audit statement explicitly cites the full names and version numbers of the audit standards and criteria used, and that they satisfy Root Store requirements. |
| `Auditor Not Found` | ALV could not find the selected auditor name in the audit statement. | • Confirm the `Auditor` selected on the CCADB record/case matches the audit firm name written in the audit statement.<br>• If both are accurate, add a Case Comment asking a Root Store Operator to update the recognized auditor name aliases in the CCADB. |
| `CA Owner Not Found` | ALV could not find the CA Owner's name (or, for intermediate records with separate audits, the `Subordinate CA Owner` value) in the audit statement. | • Confirm your `CA Owner` name in the CCADB matches the exact legal organization name stated in the audit letter (request an organizational name update on the [CA OWNER tab](updates#ca-owner) if needed).<br>• For intermediate certificates with their own audit statements, edit the `Subordinate CA Owner` field directly on the intermediate record to match the organization name in the audit statement. |
| `Download Audit Letter Fail` | The URL provided for the audit statement could not be reached or resolved. | Correct and verify the `Audit Statement (Link)` / `* Audit URL` field so it retrieves the PDF directly without authentication or broken redirects, then re-run ALV. |
| `Audit Letter Not Found In Certified Location: Audit letter should be hosted at an ALV-recognized trusted audit letter location.` | The audit statement URL does not match CCADB's list of recognized audit hosting domains (such as `cpacanada.ca` and accredited CAB websites). | • **Ignore this error** while testing preliminary audit statements hosted on Bugzilla or Google Drive.<br>• Confirm the URL uses `https://`.<br>• For final audit statements hosted on an accredited auditor/CAB domain that still trigger this message, ask the reviewing Root Store Operator in a Case Comment (including auditor contact details if authentication is needed) to add the auditor's domain to ALV's known locations. |
| `Audit Letter Not PDF` | ALV could not parse the file retrieved from the audit statement URL as a valid PDF document. | Update the audit statement URL to link directly to the raw `.pdf` file (not an HTML wrapper page or `.zip` archive). |
| `Audit statement is not text-searchable` | Some or all of the audit statement is stored as scanned images rather than searchable text. | Obtain a text-searchable PDF from your auditor in which the auditor name, CA Owner name, audit period, statement date, audit criteria, and SHA-256 certificate fingerprints are encoded as selectable text rather than images. |
