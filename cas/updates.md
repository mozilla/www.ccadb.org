# Updating Audit Statements, Policy Documents, and Other Data #

Instructions for requesting updates to CA Owner and Root Certificate records:
* [Create an Add/Update Root Request](https://docs.google.com/document/d/1ttmeeqO6WxDWe_deDNsGUgDO_LpsvoduFNZeHHMw_f8/edit?usp=sharing)

The "Add/Update Root Request" is used to provide updates to CA Owner and Root Certificate records, and to request that new root certificate records be added to the CCADB. The request case contains the following tabs, and you may choose which tabs to make updates in. For example, if you are providing policy document updates inbetween annual audits, then you may only want to update the POLICY DOCUMENTS tab.
* CA OWNER
* AUDITS
* POLICY DOCUMENTS
* ROOT INFORMATION
* TEST WEBSITES

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



