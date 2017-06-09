# CCADB Root Store Member Usage Terms #

As permitted by section 4.1 (b) of the [Common CA Database
Agreement][CCADB-Agreement], and in addition to any other requirements set out
therein, Mozilla sets some usage terms and rules for Root Store Members using
the CCADB, as follows.

## Meetings ##

Root Store Members of the CCADB may meet by teleconference or
at face-to-face meetings for the purpose of discussing improvements or changes
to the operation of the CCADB. Such discussions should not include
competitively-sensitive information. Mozilla shall not be responsible for the
expenses of any such teleconferences or meetings.

## Customizing the CCADB ##

A Root Store Member may make customization changes that only impact itself.
Before being applied to the production instance of the CCADB,
changes will be reviewed and tested by Mozilla (or its representative),
including to ensure that the changes will not negatively impact any of the
other Members or the CCADB. Mozilla will either approve or decline
the proposed changes. If the changes are approved, then a Mozilla
representative will apply the changes to the production instance of the Common
CA Database. If the changes are denied, then the Mozilla representative will
provide an explanation, and the Member organization may submit the
customizations again after addressing the feedback.

Root Store Members may request customization changes that impact shared data
and interfaces. Mozilla (or its representative) will review, and approve or
deny such requests. If the request is approved, Mozilla will prioritize the
requested changes, and work with the members to design and test the changes in
a sandbox environment before applying them to the production instance of the
CCADB.

The customizations that Mozilla has applied to the CCADB are
available on [GitHub][CCADB-Github].

## Appropriate Data ##

Root Store Members may store the following types of data in the Common CA
Database, as it pertains to the management of their root store programs:

* CA and subordinate CA certificate data;
* Contact information for CA Owners (name, phone number, email address,
  physical address, etc.);
* Contact information for Auditors;
* URLs to public-facing sites and documents;
* URLs to internal-facing sites and documents (provided the URLs are not
  confidential);
* Root-store-specific status and decisions regarding root inclusion/change
  requests;
* Dates and comments relating to root and intermediate certificates.

Root Store Members shall **not** store the following types of data in the
CCADB:

* Confidential data
* Personal (as opposed to business) contact information for individuals
* Documents, e.g. PDFs, spreadsheets, word processing documents
* Pictures, e.g. GIFs, PNGs, JPEGs

[CCADB-Agreement]: ./mozilla-ccadb-agreement.pdf
[CCADB-Github]:    https://github.com/CACommunity/Salesforce
