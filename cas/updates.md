# Submitting Annual Updates #

All CAs are required to update the audit, CP, CPS and test website information
for their certificate hierarchies at least annually. CAs are expected to
maintain their [**intermediate**](intermediates) certificate records themselves
and to directly enter the corresponding [updated audit
statements](fields#audit-information). However, **root** certificate data
cannot be self-maintained. This page describes the process for providing annual
updates for root certificates, where a CA submits data and it is validated by
a root store operator.

CAs in the CCADB are organized into hierarchies. Each CA Owner has children
nodes that are Root Certificate records, Root Certificate records have children
nodes that are Intermediate Certificate records, and Intermediate Certificate
records have children nodes that are Intermediate Certificate records. Records
and Cases are also organized in hierarchies, similar in concept to the CA
hierarchies.

**Important:** 
* Create **one** Audit Case for a particular set of audits (e.g. standard, BR, and EV). In the Audit Case you will indicate which root certificates the audit statements apply to.
* Remember to click on the ‘Audit Letter Validation [ALV]’ button when you are done providing your information, so your Audit Case will get assigned to a root store operator for processing.

## Test Preliminary Audit Statements ##

To test preliminary audit statements with ‘Audit Letter Validation (ALV)’:

1. Upload the audit statements to a [Bugzilla Bug](fields#uploading-documents), indicating that they are preliminary
2. Create an [Audit Case](updates#instructions) in the CCADB, providing links to the audit statements that were attached to the Bugzilla Bug
 * The audit statement link should like like https://bugzilla.mozilla.org/attachment.cgi?id=9147882 or https://bug1616745.bmoattachments.org/attachment.cgi?id=9147882
3. Add a Case Comment to the Audit Case that says: "Preliminary Audit Reports"
4. Follow the rest of the [instructions](updates#instructions) and run ALV on the Audit Case containing the preliminary audit statements
5. When the audit statements are finalized, update the audit links in the Audit Case, re-run ALV, and add a Case Comment that says: "Final Audit Reports"

## Instructions ##

**Video:** [How to Create an Audit Case](https://drive.google.com/file/d/1t5juvsotFexIb6Db1iYWVn6SPwqXTcqC/view?usp=sharing)

1. [Login to the CCADB](getting-started)
2. Click on the 'My CA' tab
3. Click on the 'CASES' tab under the CA Owner's name, near the top left corner of the page
4. Click on the 'NEW' button, which is on the right side of the page, below the 'GET URLs' button
5. Select 'CA Audit Update Request' (default), and click on 'Next'
6. Click on the 'Save' button. 
    * There will be a green bar shown across the top of the page, which says “Case ###### was created. Click on the number in that green bar to view the new Case.
    * Otherwise go back to the 'CASES' tab in 'My CA', and click on the number in the top row of the 'Case' column.
7. The Instructions section and Case Progress bar towards the top of the page will indicate what you need to do.
8. Click on the 'Edit' button, enter the Auditor and Audit statement information, then click on the 'Save' button.
   * Audit statements must meet the requirements listed in
    [section 5.1 of the Common CCADB Policy](https://www.ccadb.org/policy#51-audit-statement-content)
    * CCADB automatically converts WebTrust Seal URLs into PDF URLs when you click on 'Save'
    * When there are findings that prevent getting an ETSI Certificate or WebTrust Seal, you may 
    upload the document to [Bugzilla](fields#uploading-documents)
9. Click on the 'Add/Update Root Cases' button to indicate which root certificates are covered in the audit statements.
    * For each root certificate in the audit statements, check the boxes corresponding 
      to the audit statements that apply. 
      * Click on the 'Apply Changes' button
10. Click on the 'Update Policy Documents' button to provide current CP/CPS information. 
    * Click on the 'Help' button in the 'Add Policy Documents' page for instructions
    * Update existing policy document information, or add new policy documents via the 'Add Policy Document' button
    * Click on the checkmark to save each set of changes before clicking on the 'Go Back' button to return to the Case
11. Click on 'Edit Test Websites' button (which may be in the button overflow -- upside down triangle) to update test website URLs  if any of the root certificates 
covered by these audit statements can validate TLS/SSL certificates.
12.  Click on the 'Test Websites Validation' button (which may be in the button overflow -- upside down triangle) if any of the root certificates covered 
by these audit statements can validate TLS/SSL certificates.
     * Resolve all failures, then click on 'Re-run Validaton'
13.  Confirm that the information in the 'Recognized CAA Domains' and 'Problem Reporting Mechanism' fields is current and of the correct format.
     * 'Recognized CAA Domains' should be a comma-separated list of domain names
       recognized in a CAA record's 'issue' and 'issuewild' property tags as
       permitting issuance under this CA's root certificates
     * 'Problem Reporting Mechanism' should be an email address or URL for 
       reporting suspected private key compromise or certificate mis-issuance
14. Click on the 'Audit Letter Validation [ALV]' button  (which may be in the button overflow -- upside down triangle) and resolve any issues.
      

Helpful Hint: Before starting this process, it may be helpful to open another window
  showing your CA's Hierarchy, so you can easily see which root
  certificates need to be accounted for in the audit statements. Click on the 
  'My CA' tab, and then the 'CA HIERARCHY' tab.

## What Happens Next? ##

After you run ALV, your Audit Case will be assigned to a root store operator for processing.
Here is what they will do:
1. Verify that the audit statements pass ALV and meet the requirements of [section 5.1 of the Common CCADB Policy](https://www.ccadb.org/policy#51-audit-statement-content)
2. Verify the [auditor's qualifications](https://wiki.mozilla.org/CA/Audit_Statements#Auditor_Qualifications)
3. Verify the updated policy documents
4. Check that the test websites pass validation and lint testing, if applicable

When all of the information has been verified for the Audit Case and
corresponding Root Cases, the data in the Audit Case will be used to update 
the corresponding CA Owner and root certificate records in the CCADB.
