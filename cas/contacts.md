The ‘Add/Update Contacts’ case is used by a CA Owner to add new or update existing contacts for their organization directly in the CCADB.

CA Owners can have three types of contacts in the CCADB:

1. A "Primary POC" is a contact who intends to log in to CCADB. 
2. A "POC" is a contact that cannot log in to CCADB but will receive CCADB notifications. 
3. A contact who no longer needs notifications from or access to CCADB is "Obsolete".

To create a ‘Add/Update Contacts’ case in the CCADB:

1. Click on the ‘My CA’ tab.
2. Click on the ‘CASES’ tab under the CA Owner’s name, near the top left corner of the page.
3. Click on the ‘New’ button, which is on the right side of the page, below the ‘Get URLs’ button.
4. Select ‘Add/Update Contacts’, and click on ‘Next’.
5. Type in information for the ‘Subject’ (e.g., XYZ Root Certificates).
6. Click on the ‘Save’ button.
    * There will be a green bar shown across the top of the page, which says “Case ###### was created”. Click on the number in the list below (the same which was provided by green bar) to view the new case.

An expandable list of all POCs for your organization is presented in alphabetical order. Obsolete contacts are listed at the bottom with ** in front of their name.

* Detailed Instructions: [Add/Update Contacts](https://docs.google.com/document/d/1QQ-wZYPJ_3p76Zc3RZPE929pKIResc5J4vjSGGi_NuE/edit?usp=sharing)

If a CA Owner wants to stop receiving all communications from the CCADB, they can have a Primary POC log in and:

1. Create a `Add/Update Contacts` case and select `Yes` for the ‘Is this Contact Obsolete?’ field for each Primary POC and POC.  
2. Create an `Add/Update Root Request` case and on the `CA Owner` tab, remove the values for `CA Email Alias 1` and `CA Email Alias 2`.

Once a Root Store Operator reviews and syncs these cases to the CCADB, all system emails will stop.
