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

## Adding Intermediate Certificate Data ##

1. Find the root or intermediate certificate that signed the intermediate
   certificate, using one of the following methods:
   * Copy-and-paste the SHA-1 or SHA-256 fingerprint of the issuing certificate
     into the Search bar at the top of the window. Click on the name of the
     certificate to open the record.
   * Type the name of your CA or the name of the issuing certificate into the
     Search bar at the top of the window. Click on the name of the certificate
     to open the record.
   * Click on "CA Owners/Certificates" tab, then in "View:" select "Community
     User's CA Owners/Root Certs" and click on "Go!". Click on the name of the
     certificate to open the record.
2. Click on the "New Intermediate Cert" button. This will create a new record
   for an intermediate cert chaining up to the certificate record you were just
   viewing.
3. Click on the "Add/Update PEM Info" button.
4. Copy and paste the [PEM data](fields#pem-data) for the intermediate
   certificate into the resulting window. PEM data starts with
   ''-----BEGIN CERTIFICATE-----'' and ends with ''-----END CERTIFICATE-----''.
5. Click on "Validate PEM Info" button. This will invoke a program that will
   try to parse the PEM data and extract certain information.
6.  If the cert check is successful, then click on the "Update Intermediate
   Cert" button. If the cert check was not successful, then click on the
   "Cancel" button. Check that the PEM data is correct and try again, by
   clicking on the "Add/Update PEM Info" button and copy-pasting the data in.
   If it still fails, then send email to support@ccadb.org with the PEM data.
7. In the intermediate certificate record you will see that the cert data has
   been filled in. Review the filled-in information (Issuer and Subject
   information, and SHA-1 Fingerprint) to ensure it is the data you expected.
   If the data is not what you expected, then check that you have the correct
   PEM data for the certificate you intended to add. Check the section titled
   "PEM Information..." to make sure the PEM is as you intended. There should
   not be extra characters before or after the PEM, and the PEM data should not
   have extra line feeds in it. You may go through the "Add/Update PEM Info"
   process as many times as needed.
8. Fill in the information in the "[Audit
   Information](fields#audit-information)" and "[Policies and Practices
   Information](fields#policies-and-practices-information)" sections. The
   audits and policies must cover the intermediate certificate.
    * If the information is the **same as for the issuing (parent)
      certificate**, then click on the "Edit" button, and check on the **"...
      Same as Parent" check-boxes** ("CP/CPS Same as Parent" and "Audits Same
      as Parent"), then click on the "Save" button.
    * If the information **has some differences from the issuing (parent)
      certificate**, then click on the "Edit" button to enter the audit and
      policy information. Be sure to click on the "Save" button afterward. 

### Clone ###

When you are entering intermediate certificate data, and you have intermediate
certificates that share the same CP, CPS, and audit statements, then you can
use the "Clone" button to save time. The recommended procedure is as follows:

1. Enter the data for one intermediate certificate following the instructions
   above.
2. Make sure the "Audit Information" and "Policies and Practices Information"
   sections are completely and correctly filled in and saved, or that the
   "CP/CPS Same as Parent" and "Audits Same as Parent" checkboxes are set.
3. Click on the "Clone" button. This will create a new intermediate
   certificate record, copying the "Parent CA Owner/Certificate" field and the
   "Audit Information" and "Policies and Practices Information" sections.
4. Click on the "Add/Update PEM info" button, and enter the PEM data for the
   intermediate certificate data you are adding.
5. Click on the "Validate PEM Info" and "Update Intermediate Cert" buttons.
   The data for the intermediate certificate will be automatically filled in.
6. If the intermediate certificate has a different Issuer than the cert you
   had cloned, then click on the "Edit" button, change the "Parent CA
   Owner/Certificate" to the correct value (which you can copy from the Cert
   Issuer Common Name field in the page), and click on the "Save" button.

## Mass Update of Audit/CP/CPS Data ##

The "Mass Update Audit/CP/CPS Data" button may be used to apply a particular
set of changes to all intermediate certificates signed by the same parent
certificate. The certificate you are viewing when you click on the Mass Update
button will be treated as the "source", and you will have an opportunity to
make some or all of the certificates signed by the same parent match it.

To use this facility, choose an intermediate certificate to be the source, and
click on the "Mass Update Audit/CP/CPS Data" button. This button will look for
all of the certificates signed by the same parent certificate, and do the
following:

* If the "Target" certificate has different Audit or Policy information than
  the Source, then a window will display the Audit and Policy information for
  both certificates side-by-side, and the differences will be shown in blue
  text.
* If you want to update the Target certificate to have the same Audit or
  Policy information as the Source, then click on the "Yes" button in each
  section. Otherwise, click on the "Next Target Cert" button to continue to the
  next certificate.
* If you click on the "Exit" button, you can re-start the process later
  without having to go through all of the certs that you already updated. Each
  time you click on the Mass Update button, it will only show the sibling
  certificates with different Audit and Policy information.

## Marking An Intermediate Certificate As Revoked ##

The best way to add revoked intermediate certificate data to the CCADB is to
first add the intermediate certificate record as above, and then mark the
record as Revoked, as follows:

1. Find the intermediate certificate record, if you are not already viewing it.
2. Click "Edit".
3. Click the "Revocation Status" field and select "Revoked".
4. Enter the "Date of Revocation".
5. Click the "RFC 5280 Revocation Reason Code" field and select the
   corresponding revocation reason.
6. Click the "Save" button.
