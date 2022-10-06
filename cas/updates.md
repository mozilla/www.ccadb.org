# Add and Update Root Certificate Records #

The "Add/Update Root Request" case is used to request that Root Certificate records be added to the CCADB, and to request updates to CA Owner and Root Certificate records such as policy and audit updates.
* Instructions: [Create an Add/Update Root Request](https://docs.google.com/document/d/1ttmeeqO6WxDWe_deDNsGUgDO_LpsvoduFNZeHHMw_f8/edit?usp=sharing)

The "Add/Update Root Request" case contains the following tabs, and you may choose which tabs to make updates in. For example, if you are providing policy document updates inbetween annual audits, then you may only want to update the POLICY DOCUMENTS tab. 

Note: New required fields were added to Root Certificate records on September 15, 2022, and those fields will have to be filled in the next time an "Add/Update Root Request" case is used to update a pre-existing Root Certificate record. Those fields are in the "ROOT INFORMATION" tab.
* CA OWNER
* AUDITS
* POLICY DOCUMENTS
* ROOT INFORMATION
* TEST WEBSITES

To **add a Root Certificate record to the CCADB**, view the instructions for the "ROOT INFORMATION" tab. High level instructions:
1. Go to the "ROOT INFORMATION" tab
2. Click on the "Add/Select Root Certificates" button
3. Click on the "Add Root Certificate to CCADB" button
4. Paste the certificate PEM into the window and click on "Validate PEM"
5. If validation is successful, click on the "Create Root Certificate in CCADB" button
6. Fill in the data for the required fields in the "ROOT INFORMATION" tab
7. Click on the "Submit to Root Store" button

CAs in the CCADB are organized into hierarchies. Each CA Owner has children
nodes that are Root Certificate records, and Root Certificate records have children
nodes that are Intermediate Certificate records, and Intermediate Certificate
records have children nodes that are Intermediate Certificate records. 

All CAs are required to update the audit, CP, CPS and test website information
for their certificate hierarchies at least annually. CAs are expected to
maintain their [**intermediate**](intermediates) certificate records themselves
and to directly enter the corresponding [updated audit
statements](fields#audit-information). However, **root** certificate data
cannot be self-maintained, because root store operators must verify the data 
before the CA Owner or Root Certificate records are modified.



