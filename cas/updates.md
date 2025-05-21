# Add and Update Root Certificate Records #

The 'Add/Update Root Request' case is used to request that Root Certificate records be added to the CCADB, and to request updates to CA Owner and Root Certificate records such as policy and audit updates.

To **create an 'Add/Update Root Request' case** in the CCADB:
1. Click on the 'My CA' tab.
2. Click on the 'CASES' tab under the CA Owner’s name, near the top left corner of the page.
3. Click on the 'New' button, which is on the right side of the page, below the 'Get URLs' button.
4. Select 'Add/Update Root Request', and click on 'Next'.
5. Type in information for the 'Subject' (e.g. Example CA New Root Certificates).
6. Click on the 'Save' button.
    * There will be a green bar shown across the top of the page, which says “Case ###### was created". Click on the number in the list below (the same which was provided by green bar) to view the new case.
    * Otherwise, go back to the 'CASES' tab in 'My CA', and click on the number in the top row of the 'Case' column.

* Detailed Instructions: [Create an Add/Update Root Request](https://docs.google.com/document/d/1AUbwbyqCq3jR7wP0fSWjL1us9s4sZIbXGRyo_ko77QM/edit)

The 'Add/Update Root Request' case contains the following tabs, and you may choose which tabs to make updates in. For example, if you are providing policy document updates inbetween annual audits, then you may only want to update the NON-AUDIT DOCUMENTS tab. 

* CA OWNER
* AUDITS
* NON-AUDIT DOCUMENTS
* ROOT INFORMATION
* TEST WEBSITES

Note: New required fields were added to Root Certificate records on September 15, 2022, and those fields will have to be filled in the next time an 'Add/Update Root Request' case is used to update a pre-existing Root Certificate record. Those fields are in the 'ROOT INFORMATION' tab.

To **add a Root Certificate record to the CCADB**, view the instructions for the 'ROOT INFORMATION' tab. High level instructions:
1. Go to the 'ROOT INFORMATION' tab.
2. Click on the 'Add/Select Root Certificates' button.
3. Click on the 'Add Root Certificate to CCADB' button.
4. Paste the certificate PEM into the window and click on 'Validate PEM'.
5. If validation is successful, click on the 'Create Root Certificate in CCADB' button.
6. Fill in the data for the required fields in the 'ROOT INFORMATION' tab.
7. Click on the 'Submit to Root Store' button.

CAs in the CCADB are organized into hierarchies. Each CA Owner has children nodes that are Root Certificate records, and Root Certificate records have children nodes that are Intermediate Certificate records, and Intermediate Certificate records have children nodes that are Intermediate Certificate records. 

Note: The CCADB considers the terms "intermediate" and "subordinate" synonymous.

All CAs are required to update the audit, policy document, and test website information for their certificate hierarchies at least annually. CAs are expected to maintain their [**intermediate**](intermediates) certificate records themselves and to directly enter the corresponding [updated audit statements](fields#audit-information). However, **root** certificate data cannot be self-maintained, because Root Store Operators must verify the data before the CA Owner or Root Certificate records are modified.

CA Owners may want to [test preliminary audit statements](https://docs.google.com/document/d/12U4az-hjYDC_aWsVn8-Y5vVmJ10inVziAxrQoxP-hfI/edit#bookmark=id.n8g8lgkwb4co) before receiving and uploading the final audit statements from their auditor to ensure the documents will pass ALV.
