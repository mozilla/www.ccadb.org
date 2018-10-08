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

The process for submitting an annual update is as follows: **CAs will create a
single Audit Case for a particular set of audits (e.g. WebTrust CA, WebTrust
BR, and WebTrust EV). Then the CA will create a set of corresponding Root
Cases, one per root, to tell the CCADB which Root Certificate records the
audit statements in that Audit Case apply to.**

## Audit Case Workflow ##

To provide annual audit statements, the CA does the following:

1. Create an Audit Case in the CCADB - one Audit Case per set of audit statements.
2. Fill in the Auditor, Audit Information, and CP/CPS Information sections.
3. Click on the ‘Add/Update Root Cases’ button to indicate which root certificates are covered in the audit statements, and which audit statements apply to each of those roots.
4. Click on the ‘Edit Test Websites’ button to make sure the test websites are correct.
5. Click on the ‘Audit Letter Validation (ALV)’ button, and work with your auditor to resolve all problems.

After ALV is run, the Audit Case gets automatically assigned to a Root Store Operator for review and final processing.

## Information Required ##

Please have the following information prepared before you begin entering your
annual update into the CCADB.

1. Links to your audit statements in PDF format.
2. Links to your CP/CPS documents in PDF format.
   * CP/CPS documents must be updated each year, with a revised version number
     even if there are no other changes.
3. Links to 3 Test websites (valid, expired, and revoked) for each root
   certificate that has the TLS/SSL trust bit enabled.
   * The existence of these websites is a requirement of the [BRs][BRs],
     section 2.2.
   * valid = unexpired and unrevoked
   * expired = notAfter less than the current day, and unrevoked
   * revoked = unexpired, but present in either/both of the CRL and OCSP
     responder

All audit, CP and CPS documents must:

* Have links which change each year, so that the audit archiving process will
  pick up the new version of the files.
* Be PDF files smaller than 25MB.
* Be in English.

If you don't have a good place to put audit, CP and CPS documents, you can
use [Bugzilla](fields#uploading-documents).

## Instructions ##

1. [Login to the CCADB](getting-started).
2. There are two ways to create an Audit Case to provide your annual updates.
   * Option 1) Click on "Cases" tab, then click on the 'Create New Case'
     button.
   * Option 2) Navigate to the CA Owner Record for your CA.
     * Click on "CA Owners/Certificates" tab, then in "View:" select
       "Community User's CA Owners/Root Certs" and click on "Go!". This will
       list the CA Owner and all of the root certificates associated with your
       account. Click on the "CA Owner/Certificate Name" of your CA's Owner
       record.
     * Scroll down to the 'Cases' section.
     * At the top of the page, just above "CA Owner/Certificate Detail" there
       are links to each of the sections, so you can click on the "Cases" link
       to go to that section.
     * Click on the 'New Case' button.
3. Click on the 'Submit' button to create the new 'Audit Case'.
   * For our use, the 'Submit' button is the 'Save' button. (Salesforce
     doesn't currently let us change the name of this particular button.)
   * The 'Subject' will be automatically filled in when you click on the
     'Submit' button, so leave it blank to begin with. You can change it later
     if needed.
   * The 'Recognized CAA Domains' and 'Problem Reporting Mechanism' fields will
     be automatically filled in when you click on the 'Submit' button, so leave
     them blank to begin with. You can change them later if needed.
4. Click on the 'Edit' button and enter the audit and CP/CPS information, then
   click on the 'Submit' button. You may click on 'Edit' and 'Submit' as many
   times as you need to get all of your information entered.
5. After you have provided the audit and CP/CPS information, you will need to
   tell us which root certificates are covered by these audits.
6. Click on the ‘Add/Update Root Cases’ button to indicate which root
   certificates are covered in the audit statements. For each covered root
   certificate, check the boxes corresponding to the audit statements that
   apply. Then click on the "Apply Changes" button. This will create
   corresponding Root Cases.
7. If any of the root certificates covered by these audit statements can
   validate TLS/SSL certificates, then you need to also provide the URLs to
   the test websites. If the root certificate is enabled for EV treatment,
   then the TLS/SSL certs for the test websites must also be EV.
    * Click on the 'Edit Test Websites' button, update the URLs to the 3 test websites for each root certificate, and click on 'Apply Changes'.
8.  Check that the information in the 'Recognized CAA Domains' and 'Problem
    Reporting Mechanism' fields is current and of the correct format.
    * 'Recognized CAA Domains' should be a comma-separated list of domain names
      recognized in a CAA record's 'issue' and 'issuewild' property tags as
      permitting issuance under this root certificate.
    * 'Problem Reporting Mechanism' should provide brief instructions for
      reporting suspected misissuance, private key compromise, information
      inaccuracy or other types of problem relating to certificates issued
      under this root certificate.

Helpful Hints:

* Before starting this process, it may be helpful to open another window
  showing your CA's Account Hierarchy, so you can easily see which root
  certificates need to be accounted for in the audit statements. Navigate to
  your CA Owner record or any of your root or intermediate cert records, go to
  the 'Account Hierarchy' section, and right-click on any of the record names
  and 'Open Link in New Window'.

* In the Root Case page, when you click on the search icon next to the
  'Included Certificate' field, the default list will be the records that you
  recently viewed.

## What Happens Next? ##

After you create the Audit Case and corresponding Root Cases, a root store
operator will review and verify the information. For your information, here's
what they verify:

* The Auditor is an independent and qualified auditor, and that the provided
  "Auditor Website" provides sufficient information about the auditor.
* The website provided for "Auditor Qualifications" is an acceptable authority,
  and that the Auditor is listed on that website as authorized for the country
  in which the Auditor's offices are located.
* The name in the "Management Assertions By" field matches the name of the
  Organization that wrote the Management Assertions for the Standard Audit.
* All audit statement links point to PDF files, and are new links (so audit
  archiving will pick up the new audits).
* Audit statement PDF files are less than 25MB, so the audit archiving program
  will accept them.
* If an audit statement is not on the webtrust.org site or the auditor's site,
  independently contact the auditor to confirm the authenticity of the audit
  statement.
* The dates all match the dates listed in the audit statements.
* The Audit Statement Date must be either the date of the audit statement or
  90 days from the end of the audit period (whichever date is closest to the
  end of the audit period).
* The CP/CPS document(s) provide the necessary information for the
  corresponding root certificates, including appropriate validation procedures.
* The CP/CPS documents were updated some time in the last year.
* The CP/CPS Last Updated Date matches the dates in the CP/CPS document(s).
* All of the root certificates in the listed Root Cases are specifically
  referenced in the audit statements.
  * If a listed Root Case has "BR Audit" selected, then confirm that root
    certificate is specifically mentioned in the BR audit statement.
  * If a listed Root Case has "EV Audit" selected, then confirm that root
    certificate is specifically mentioned in the EV audit statement.
* In each listed Root Case confirm that:
  * The appropriate audits have been selected, corresponding to all of the
    Root Store Status (i.e.trust bits, EV Policy OID)
  * The test websites have TLS/SSL certs chaining up to the corresponding root
    certificate specified in the Root Case, and that they function as expected
    (valid, expired, revoked):
    * When you browse to 'Test Website - Valid', the connection is successful.
    * When you browse to 'Test Website - Revoked' the revoked cert error is
      shown.
    * When you browse to 'Test Website - Expired' the expired cert error is
      shown.
    * For all three test websites, the certificate chains up to the relevant
      root certificate.
  * If the EV SSL audit statement is selected for the root cert, then the
    TLS/SSL certs in the test websites must be EV; i.e. have the EV Policy
    OID(s).

When all of the information has been verified for the 'Audit Case' and
corresponding Root Cases ("Request Status" is 'Data Verified' for all of
them), a root store operator will click on a 'Sync AuditUpdateInfo' button
that will propagate the audit, CP/CPS, and test website data to root
certificate records corresponding to each of the Root Cases. The root store
operator will be taken through a series of pages that look similar to the
'Mass Update Audit/CP/CPS Data' button on certificate records.

In the updated root certificate records, each time an audit statement link is
changed, the corresponding audit archive status is changed to "Not Processed".
The next time the File Archive program is run, the audit statement will be
imported and saved in the CCADB.

[BRs]: https://cabforum.org/baseline-requirements-documents/
