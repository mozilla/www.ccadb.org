# CCADB Public Group #

The public@ccadb.org [group](https://groups.google.com/a/ccadb.org/g/public) exists to discuss topics related to Certification Authorities (CAs) and Root Store Programs who use the Common CA Database (CCADB). The CCADB Steering Committee was established to provide governance and is committed to fostering a diverse, equitable, inclusive, and welcoming community. This [code of conduct](https://docs.google.com/document/d/19ALqEvHtTE6OUTz2FaOXrU9gruIdvia5EDh3hXeGpZA/edit) aids in achieving that commitment and applies to the public@ccadb.org group, as well as any private communication initiated in the context of this group. Everyone contributing to the CCADB public group must follow this code of conduct, regardless of affiliation or position.

This page details the process and procedures for conducting discussion within the group as defined by the CCADB Steering Committee. 

## CCADB Updates ##
An update to CCADB may include the addition of new functionality, the removal of previous functionality, or changes to the general availability of the system. A Root Store Member can post a message to public@ccadb.org to describe the type of update being made to CCADB.

## Root Store Program Announcements ##
The corresponding Root Store Member may post announcements related to their program in the public@ccadb.org group. The Root Store Member may describe what is changing or has changed with the program, link to supporting documentation, and any other information it feels should be communicated publicly.

## CCADB Policy Updates ##
The CCADB [policy](https://www.ccadb.org/policy) may be updated by the CCADB Steering Committee. A Root Store Member may post an update to the policy in the public@ccadb.org group. The Root Store Member may describe what is changing or has changed with the CCADB policy, link to supporting documentation, and state the effective date of the change.

## Lessons Learned from CA Incident Reports ##
An important goal of incident reporting is to help all of us work together to build a more secure web. Therefore, [incident reports](https://wiki.mozilla.org/CA/Incident_Dashboard) should include lessons learned that could be helpful to all CAs to build better systems, and those lessons learned should be shared in the public@ccadb.org group.

## Root Inclusion Public Discussion ##
For those root stores that have public discussion, public@ccadb.org enables a single, shared public discussion phase for a CA owner applying to such Root Store Programs. The CCADB root inclusion public discussion process promotes openness and transparency for applicants to public root stores. However, Root Store Programs will make final inclusion decisions independently, on their own timelines, and based on each Root Store Member’s inclusion criteria.

### Prerequisites ###
Prior to a Root Store Member initiating a CCADB root inclusion public discussion, the following must occur:

1. A CA owner must have an account in CCADB.
2. A completed 'Add/Update Root Request' case must exist in CCADB for the root CA certificate(s). A completed case must include all required information set forth in each of the following tabs in the case: CA Owner, Audits, Policy Documents, Root Information, and if applicable, Test Websites. Specifically, required "Root Information" is:
    * Background information that identifies why the CA needs to be considered for inclusion and the unique function of the CA.
    * The full CRL issued by the CA, or when there is no full CRL for the certificates issued by this CA, a JSON array whose elements are URLs of partial CRLs that when combined are the equivalent of a full CRL for the certificates issued by the CA.
    * All "PKI Hierarchy Information", which details:
        * If the CA is cross-signed by another CA and/or another CA owner,
        * If the CA has externally operated subordinate CAs,
        * If the CA has external Registration Authorities,
        * A description of the hierarchy (which can be a URL that provides the description),
        * The intended use cases (i.e. EKUs) to be served under the CA hierarchy,
        * The CA/Browser Forum Certificate Policy Identifiers included in certificates below the CA (if applicable), and
        * The TLS certificate validation methods that are available for use for certificates below the CA (if applicable).
    * A link to a completed [self assessment](https://www.ccadb.org/cas/self-assessment) for the CA.
    * A link to a Key Generation Audit Report for the CA.
3. A 'Root Inclusion Request' case must have been submitted in CCADB, and one or more Root Store Members must be selected for inclusion.

### Initiation ###
No more than three concurrent CCADB root inclusion public discussions shall take place at any given time. If more than three 'Root Inclusion Request' cases have been submitted in CCADB, any requests for replacing an existing root CA certificate in CCADB will be prioritized for public discussion. Otherwise, CCADB public discussion will generally occur on a first-ready, first-out basis (to be ready for discussion). 

A Root Store Member will initiate a six-week CCADB root inclusion public discussion in the public@ccadb.org group and provide information about the inclusion request from CCADB.

A CA owner is expected to respond to questions and concerns posted during the public discussion of their root CA certificate(s) inclusion request.

### Conclusion ###
At the end of the six-week period, the CCADB root inclusion public discussion may be continued by the Root Store Member to complete ongoing discussions or matters under investigation. If public discussion is continued, the Root Store Member will state the additional amount of time (in weeks) that the conversation may continue. Otherwise, the CCADB public discussion concludes.

The Root Store Member who initiated the public discussion provides a summary noting any objections or open questions that did not receive a response from the CA owner and states the public discussion period has concluded.

## Cross-Certificate Requests ##
Individual Root Store Program policies may require CA owners to notify public@ccadb.org before issuing a cross-certificate that can validate to a corresponding root CA certificate in the Root Store Member’s trust store. If required, the Root Store Program policy should stipulate the content required in the notification.
