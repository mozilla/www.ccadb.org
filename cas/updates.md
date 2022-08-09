# Updating Audit Statements, Policy Documents, and Other Data #

CAs in the CCADB are organized into hierarchies. Each CA Owner has children
nodes that are Root Certificate records, Root Certificate records have children
nodes that are Intermediate Certificate records, and Intermediate Certificate
records have children nodes that are Intermediate Certificate records. 

All CAs are required to update the audit, CP, CPS and test website information
for their certificate hierarchies at least annually. CAs are expected to
maintain their [**intermediate**](intermediates) certificate records themselves
and to directly enter the corresponding [updated audit
statements](fields#audit-information). However, **root** certificate data
cannot be self-maintained, because root store operators must verify the data 
before the CA Owner or Root Certificate records are modified.

Instructions for requesting updates to CA Owner and Root Certificate records:
* [Create an Audit Case](https://docs.google.com/document/d/1tVsWCHmpaizpOAgYc_xYDBMq_RBzWPjD_sP6FqNX5y0/edit?usp=sharing)
     * This Case type is used to provide audit statements for root certificates.

* [Create an Information Update Request (Non-Audit) Case](https://docs.google.com/document/d/14znpyOxbMN-itMhTCV5PxbzqmyNlmpqVZvvXjT8exk8/edit?usp=sharing)
     * This Case type is used for updating data in CA Owner and Root Certificate records between annual audit updates. 
