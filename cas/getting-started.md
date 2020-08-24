# Getting Started with the CCADB #

## Logging In ##

After you receive email with your CA Community License, you may login to the
Common CA Database as follows:

1. Browse to [the Login page][CCADB-Login]
2. Enter your Username (the email address for which your CA Community License
   was issued)
3. Enter the Password that you set up during first access
4. Click on the "Log In" button

## Navigating the Interface ##

Upon initial login you will see a row with seven tabs: "Home", "My CA", "CA
Owners/Certificates", "Contacts", "Cases", "CA Communications" and "Reports".

Important: The View in tabs and search defaults to recently viewed items only.
You must select a View or start a search and click on the 'Go!' button to
see the full set of data you are looking for.

**My CA**: Click on the "My CA" tab to see the information that is in the CCADB
for your CA, a hierarachy of root certiicates and intermediate certificates,
and who the Points of Contact are for your CA.

**CA Owners/Certificates**: Click on the "CA Owners/Certificates" tab, then in
"View:" select "Community User's CA Owners/Root Certs" and click on "Go!".
This will list the CA Owner and all of the root certificates associated with
your account. Click on the "CA Owner/Certificate Name" to view each record.
Within the record you will see an Account Hierarchy section, where you can
click on each root or intermediate certificate record to view the certificate
data.

**Contacts**: Click on the "Contacts" tab, then in "View:" select "All
Contacts" and click on "Go!". Click on the Name to view each contact record.

**Cases**: This tab is used to create and update Audit Cases for submitting
[annual updates](updates).

**CA Communications**: The "CA Communications" tab may be used when a root
store operator polls their CA members for information. You may ignore this tab
until you receive email from a root store operator asking you to respond to
such a poll.

**Reports**: Click on the "Reports" tab, then click on the "CA Community
Reports" link along the left column, then click on one of the reports in the
list. Whenever you click on the "Reports" tab it will list the reports that
you have recently viewed. You will need to click on the "CA Community Reports"
link to see all of the reports that are available to you.

Important Notes:

* Each Owner/Certificate record has a "CA Owner/Certificate Name" field. For a
  certificate record, the value of this field is usually the Certificate
  **Subject** Common Name of the certificate. For a CA Owner record, this
  field displays the CA's name. It is unfortunately not possible to
  contextually change the title of the field in the page.
* Each Certificate record has a "Parent CA Owner/Certificate" field. For an
  intermediate certificate record the value of the field should be the
  Certificate **Issuer** Common Name. For a root certificate record the value
  of the field will be the name of the CA owner. It is unfortunately not
  possible to contextually change the title of the field in the page.
* CA Community Users cannot modify the records for Owner, Root Certificate,
  and Contact. Only the Root Store Members can modify these records.
* CA Community Users can only modify the intermediate certificate records for
  their CA.

[CCADB-Login]: https://ccadb.force.com/
