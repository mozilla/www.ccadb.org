# Getting Started with the CCADB #

## Requesting a License ##

To get access to the CCADB, you need a "CA Community License". These usage licenses are granted to any CA participating in at least one of the root store programs of the participating root store operators. You only need one CA Community License to access the CCADB data relating to all participating root store programs.

If you believe that you should have a CCADB license but you have not received one, then please send email to support@ccadb.org with your name and the name of the CA you represent.

## Logging In ##

After you receive email with your CA Community License, you may login to the Common CA Database as follows:

1.  Browse to: [https://ccadb.force.com](https://ccadb.force.com)
1.  Enter your Username (the email address for which your CA Community License was issued)
1.  Enter the Password that you set up during first access
1.  Click on the "Log In" button

## Navigating the Interface ##

Upon initial login you will see a row with five tabs: "Home", "CA Owners/Certificates", "Contacts", "CA Communications" and "Reports".

**CA Owners/Certificates**: Click on the "CA Owners/Certificates" tab, then in "View:" select "Community User's CA Owners/Root Certs" and click on "Go!". This will list the CA Owner and all of the root certificates associated with your account. Click on the "CA Owner/Certificate Name" to view each record. Within the record you will see an Account Hierarchy section, where you can click on each root or intermediate certificate record to view the certificate data. 

**Contacts**: Click on the "Contacts" tab, then in "View:" select "All Contacts" and click on "Go!". Click on the Name to view each contact record. 

**CA Communications**: The "CA Communications" tab may be used when a root store operator polls their CA members for information. You may ignore this tab until you receive email from a root store operator asking you to respond to such a poll. 

**Reports**: Click on the "Reports" tab, then click on the "CA Community Reports" link along the left column, then click on one of the reports in the list. Whenever you click on the "Reports" tab it will list the reports that you have recently viewed. You will need to click on the "CA Community Reports" link to see all of the reports that are available to you.

Important Notes:

* Each Owner/Certificate record has a "CA Owner/Certificate Name" field. For a certificate record, the value of this field is usually the Certificate '''Subject''' Common Name of the certificate. For a CA Owner record, this field displays the CA's name. It is unfortunately not possible to contextually change the title of the field in the page.
* Each Certificate record has a "Parent CA Owner/Certificate" field. For an intermediate certificate record the value of the field should be the Certificate '''Issuer''' Common Name. For a root certificate record the value of the field will be the name of the CA owner. It is unfortunately not possible to contextually change the title of the field in the page.
* CA Community Users cannot modify the records for Owner, Root Certificate, and Contact. Only the Root Store Members can modify these records.
* CA Community Users can only modify the intermediate certificate records for their CA.
* When PEM data is provided, the certificate details in the record may not be modified.

## PEM Data ##

The CCADB accepts certificate information in the [PEM](https://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions) format. PEM is a container format defined in RFCs [1421](https://tools.ietf.org/html/rfc1421) to [1424](https://tools.ietf.org/html/rfc1424). PEM actually means Privacy Enhanced Mail, but the container format it uses is a Base64 translation of [X.509](https://en.wikipedia.org/wiki/X.509) [ASN.1](https://en.wikipedia.org/wiki/Abstract_Syntax_Notation_One) keys.

[Mozilla's TLS Observatory Certificate Explainer](https://tls-observatory.services.mozilla.com/static/certsplainer.html) may be used to convert a certificate in any other format into PEM, as follows:

* Visit the [Certificate Explainer](https://tls-observatory.services.mozilla.com/static/certsplainer.html).
* In the 'Post a certificate' section click on the 'Browse...' button to select a .cer, .crt, .cert, or .pem file.
* Check the top of the window to make sure there are no errors listed, and that the desired certificate has been found.
* The data in the text box in the 'Post a certificate' section is the PEM. 
* Copy and past the entire PEM blob, which starts with "-----BEGIN CERTIFICATE-----" and ends with "-----END CERTIFICATE-----", into the CCADB.
