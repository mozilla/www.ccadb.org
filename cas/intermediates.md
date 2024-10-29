# Managing Intermediate Certificates #

CA Owners can view root and intermediate certificate data for all of the CAs in
CCADB. However, CA Owners may only directly modify the intermediate certificate
records for certificates chaining up to root certificates they own.

Note: The CCADB considers the terms "intermediate" and "subordinate" synonymous.

CA Owners should consult the [CCADB Policy](/policy#4-intermediate-certificates)
about the requirements for disclosing intermediate certificate data 
in the CCADB.

Instructions for updating CA Owner or root certificate data in the CCADB are 
[here](updates).

Table of Contents:
1. [Updating Audit Statements](intermediates#updating-audit-statements)
2. [Adding Intermediate Certificate Data](intermediates#adding-intermediate-certificate-data)
3. [API](intermediates#api)
4. [Mass Update of Audit/Non-Audit Info](intermediates#mass-update-of-audit-non-audit-info)
5. [Marking An Intermediate Certificate As Revoked](intermediates#marking-an-intermediate-certificate-as-revoked)

## Updating Audit Statements ##

All CA Owners are required to update the audit and CP/CPS information for their 
certificate hierarchies at least annually. CA Owners are expected to maintain their 
intermediate certificate records themselves and to directly enter the 
corresponding updated audit statements via the following instructions. 
Audit information for root certificate records must be provided via an 
[Add/Update Root Request Case](updates).

**Important:** If the audit statements for an intermediate certificate are the 
same as the certificate that signed it, then check the 'Audits Same as Parent' 
checkbox instead of providing separate audit information.

1. [Login to the CCADB](getting-started).
2. Navigate to the intermediate certificate record. Here are some ways to do that:
* The CA Task List on your CCADB home page has a report called "Intermediate
Certificates with Outdatated Audit Statements". You can click on the certificate link
to browse to each record listed within that report.
* Click on the 'My CA' tab, then click on the 'CA HIERARCHY' tab underneath the CA
Owner name in the upper left corner of the page.
* Click on the magnifying glass icon next to your name in the upper right corner
   of the page, and enter the SHA-1 or SHA-256 fingerprint of the intermediate certificate,
   then hit return.
3. In the intermediate certificate page click on the 'Edit' button and enter the 
[audit and CP/CPS information](fields), then click on the 'Save' button.
4. Optional: Click on the [Mass Update Audit/Non-Audit Info](intermediates#mass-update-of-audit-non-audit-info) button to apply changes to other intermediate certificates in the same hierarchy, if applicable.

## Adding Intermediate Certificate Data ##

1. Find the root or intermediate certificate that signed the new intermediate
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
5. If the cert check is successful, then click on the 'Update Intermediate
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
7. Fill in the information in the '[Audit Information](fields#audit-information)' and '[Non-Audit
   Information](fields#non-audit-information)' sections. The
   audits and policies must cover the intermediate certificate.
    * IMPORTANT: If the information is the **same as for the issuing (parent)
      certificate** (or a subset), then check 'Audits Same as Parent', 'CP Same as Parent', 'CPS Same as Parent', and or 'CP/CPS Same as Parent'.
    * If the information **has some differences from the issuing (parent)
      certificate**, then click on the 'Edit' button to enter the audit and
      policy information. Be sure to click on the 'Save' button afterward. 

### Clone ###

When you are entering intermediate certificate data, and you have intermediate
certificates that share the same CP, CPS, or CP/CPS, and audit statements, then you can
use the 'Clone' button to save time. The recommended procedure is as follows:

1. Enter the data for one intermediate certificate following the instructions
   above.
2. Make sure the 'Audit Information' and 'Policies and Practices Information'
   sections are completely and correctly filled in and saved, or that the
   'CP Same as Parent', 'CPS Same as Parent', or 'CP/CPS Same as Parent' and 'Audits Same as Parent' checkboxes are set.
3. Click on the 'Clone' button. This will create a new intermediate
   certificate record, copying the 'Parent CA Owner/Certificate' field and the
   'Audit Information' and 'Non-Audit Information' sections.
4. Click on the 'Add/Update PEM info' button, and enter the PEM data for the
   intermediate certificate data you are adding.
5. Click on the 'Validate PEM Info' and 'Update Intermediate Cert' buttons.
   The data for the intermediate certificate will be automatically filled in.
6. If the intermediate certificate has a different Issuer than the cert you
   had cloned, then click on the 'Edit' button, change the 'Parent CA
   Owner/Certificate' to the correct value, and click on the 'Save' button.

## API ##

[CCADB APIs](https://github.com/mozilla/CCADB-Tools/tree/master/API_AddUpdateIntermediateCert) 
have been developed to enable CA Owners to automate retrieving and updating intermediate 
certificate data in the CCADB. This service is only available 
to CA Owners whose root certificates are included within the root stores 
of CCADB Root Store Operators.
* GetCertificateIdAPI: Returns the root or intermediate certificate record Id (Salesforce Id) in the CCADB.
* AddUpdateIntermediateCertAPI: Add or update an intermediate certificate record in the CCADB.


## Mass Update of Audit/Non-Audit Info ##

The 'Mass Update Audit/Non-Audit Info' button may be used to apply a particular
set of changes to all intermediate certificates signed by the same parent
certificate. The certificate you are viewing when you click on the Mass Update
button will be treated as the "source", and you will have an opportunity to
make some or all of the certificates signed by the same parent match it.

To use this facility, choose an intermediate certificate to be the source, and
click on the 'Mass Update Audit/Non-Audit Info' button. This button will look for
all of the certificates signed by the same parent certificate, and do the
following:

* If the "Target" certificate has different Audit or Non-Audit information than
  the Source, then a window will display the Audit and Non-Audit information for
  both certificates side-by-side, and the differences will be shown in blue
  text.
* If you want to update the Target certificate to have the same Audit or
  Non-Audit information as the Source, then click on the 'Yes' button in each
  section. Otherwise, click on the 'Next Target Cert' button to continue to the
  next certificate.
* If you click on the 'Exit' button, you can re-start the process later
  without having to go through all of the certs that you already updated. Each
  time you click on the Mass Update button, it will only show the sibling
  certificates with different Audit and Non-Audit information.

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
