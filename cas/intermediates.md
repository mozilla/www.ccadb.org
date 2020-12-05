# Managing Intermediate Certificates #

CAs can view root and intermediate certificate data for all of the CAs in
CCADB. However, CAs may not modify any root certificate data, or intermediate
certificate data for certificates chaining up to roots they do not own.

All changes to root certificates must go through the root store operator's
root inclusion/change process. If you need to update CP/CPS, audit, or Point
of Contact data for your root certificate(s) send email to an appropriate root
store operator.

CAs should consult the [Common CCADB Policy](/policy) to know which
intermediate certificates are required to be added to the CCADB.

## Updating Audit Statements ##

All CAs are required to update the audit and CP/CPS information for their 
certificate hierarchies at least annually. CAs are expected to maintain their 
intermediate certificate records themselves and to directly enter the 
corresponding updated audit statements via the following instructions. 
Audit information for root certificate records must be provided via an 
[Audit Case](updates).

**Note:** If the audit statements for an intermediate certificate are the 
same as the certificate that signed it, then check the 'Audits Same as Parent' 
checkbox instead of providing separate audit information.

1. [Login to the CCADB](getting-started).
2. Navigate to the intermediate certificate record. Here are some ways to do that:
* Click on the 'My CA' tab, then click on the 'CA HIERARCHY' tab underneath the CA
Owner name in the upper left corner of the page.
* Click on the 'Reports' tab, then click on 'All Folders', then click on 'CA Community 
Reports', and click on the 'My Outdated Audit Statements for ICs' report. This
report has links to your CA's intermediate certificate records that need to be updated.
* Click on the magnifying glass icon next to your name in the upper right corner
   of the page, and enter the SHA-1 or SHA-256 fingerprint of the intermediate certificate,
   then hit return.
3. In the intermediate certificate page click on the 'Edit' button and enter the 
[audit and CP/CPS information](fields), then click on the 'Save' button.
4. Optional: Click on the 'Mass Update Audit/CP/CPS Data' button to apply changes to other intermediate certificates in the same hierarchy, if applicable.

## Adding Intermediate Certificate Data ##

1. Find the root or intermediate certificate that signed the intermediate
   certificate, using one of the following methods:
   * Click on the 'My CA' tab, then click on the 'CA HIERARCHY' tab underneath the CA
   Owner name in the upper left corner of the page.
   * Click on the magnifying glass icon next to your name in the upper right corner
      of the page, and enter the SHA-1 or SHA-256 fingerprint of the certificate,
      then hit return.
2. Click on the 'New Intermediate Cert' button towards the upper right corner
   of the page. 
3. Copy and paste the [PEM data](fields#pem-data) for the intermediate
   certificate into the resulting window. PEM data starts with
   ''-----BEGIN CERTIFICATE-----'' and ends with ''-----END CERTIFICATE-----''.
4. Click on 'Validate PEM Info' button. This will invoke a program that will
   try to parse the PEM data and extract certain information.
5.  If the cert check is successful, then click on the 'Update Intermediate
   Cert' button. If the cert check was not successful, then click on the
   'Cancel' button. Check that the PEM data is correct and try again.
   If it still fails, then send email to support@ccadb.org with the PEM data.
6. In the intermediate certificate record you will find the certificate data
   in the 'Certificate Data...' section. Review the information to ensure it is 
   the data you expected. If the data is not what you expected, then check 
   that you have the correct PEM data for the certificate you intended to add
   by checking the section titled 'PEM Information...'. There should
   not be extra characters before or after the PEM, and the PEM data should not
   have extra line feeds in it. If you need to update the PEM, use the 
   button called 'Add/Update PEM Info' which may be found in the button overflow
   (upside down triangle) in the upper right corner of the page.
7. Fill in the information in the '[Audit Information](fields#audit-information)' and '[Policies and Practices
   Information](fields#policies-and-practices-information)' sections. The
   audits and policies must cover the intermediate certificate.
    * IMPORTANT: If the information is the **same as for the issuing (parent)
      certificate** (or a subset), then check 'Audits Same as Parent' and 'CP/CPS Same as Parent'.
    * If the information **has some differences from the issuing (parent)
      certificate**, then click on the 'Edit' button to enter the audit and
      policy information. Be sure to click on the 'Save' button afterward. 

### Clone ###

When you are entering intermediate certificate data, and you have intermediate
certificates that share the same CP, CPS, and audit statements, then you can
use the 'Clone' button to save time. The recommended procedure is as follows:

1. Enter the data for one intermediate certificate following the instructions
   above.
2. Make sure the 'Audit Information' and 'Policies and Practices Information'
   sections are completely and correctly filled in and saved, or that the
   'CP/CPS Same as Parent' and 'Audits Same as Parent' checkboxes are set.
3. Click on the 'Clone' button. This will create a new intermediate
   certificate record, copying the 'Parent CA Owner/Certificate' field and the
   'Audit Information' and 'Policies and Practices Information' sections.
4. Click on the 'Add/Update PEM info' button, and enter the PEM data for the
   intermediate certificate data you are adding.
5. Click on the 'Validate PEM Info' and 'Update Intermediate Cert' buttons.
   The data for the intermediate certificate will be automatically filled in.
6. If the intermediate certificate has a different Issuer than the cert you
   had cloned, then click on the 'Edi' button, change the 'Parent CA
   Owner/Certificate' to the correct value (which you can copy from the Cert
   Issuer Common Name field in the page), and click on the 'Save' button.

### Mass Import ###

CAs who have a large number of intermediate certificates to add to the CCADB may request that their data be mass imported from a spreadsheet or CSV file, by sending email to their root store operator. Doing the [mass import process](massimport) involves a significant amount of manual work, so if you have less than 20 intermediate certificates please enter them by hand.

## Mass Update of Audit/CP/CPS Data ##

The 'Mass Update Audit/CP/CPS Data' button may be used to apply a particular
set of changes to all intermediate certificates signed by the same parent
certificate. The certificate you are viewing when you click on the Mass Update
button will be treated as the "source", and you will have an opportunity to
make some or all of the certificates signed by the same parent match it.

To use this facility, choose an intermediate certificate to be the source, and
click on the 'Mass Update Audit/CP/CPS Data' button. This button will look for
all of the certificates signed by the same parent certificate, and do the
following:

* If the "Target" certificate has different Audit or Policy information than
  the Source, then a window will display the Audit and Policy information for
  both certificates side-by-side, and the differences will be shown in blue
  text.
* If you want to update the Target certificate to have the same Audit or
  Policy information as the Source, then click on the 'Yes' button in each
  section. Otherwise, click on the 'Next Target Cert' button to continue to the
  next certificate.
* If you click on the 'Exit' button, you can re-start the process later
  without having to go through all of the certs that you already updated. Each
  time you click on the Mass Update button, it will only show the sibling
  certificates with different Audit and Policy information.

## Marking An Intermediate Certificate As Revoked ##

The best way to add revoked intermediate certificate data to the CCADB is to
first add the intermediate certificate record as above, and then mark the
record as Revoked, as follows:

1. Find the intermediate certificate record, if you are not already viewing it.
2. Click 'Edit'.
3. Click the 'Revocation Status' field and select 'Revoked'.
4. Enter the 'Date of Revocation'.
5. Click the 'RFC 5280 Revocation Reason Code' field and select the
   corresponding revocation reason.
6. Click the 'Save' button.
