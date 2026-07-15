# CCADB Usage Guidelines #

This page is intended for CA Owners who have requested and obtained access to the CCADB. We look forward to your help in keeping your CA’s data up-to-date in the CCADB, and ask that you follow these usage guidelines.

## CCADB Accounts and Logins

The CCADB supports different types of accounts to facilitate management and communication while optimizing license usage.

### Primary POCs (Production Login Accounts)

Each CA Owner should:

*   **Designate a Primary POC:** Designate an individual who requires regular login access to manage the CA Owner's CCADB records. An individual with login credentials to the CCADB is referred to as a **Primary Point of Contact (Primary POC)**.
*   **Designate Additional Primary POCs:** Designate at least one additional Primary POC so that another authorized individual can access the CCADB if the Primary POC who normally manages the CA Owner's records is unavailable. To manage Salesforce Community license costs, **each CA Owner is limited to a maximum of 5 Primary POC (login) accounts**. 
*   **Manage Login Frequency:** Limit usage to less than 5 *daily-unique-logins* per month on average (approximately once per week). We understand some months require more activity to update data, this is why we monitor average usage. Salesforce counts one login for each 24-hour period that a Primary POC logs into the CCADB, this is referred to as a daily-unique-login. The CCADB Steering Committee member organizations are currently paying for a monthly allotment of daily-unique-logins for CAs. Salesforce follows a yearly entitlement policy to determine the number of used daily-unique-logins (i.e., our monthly allotment multiplied by 12), which resets annually on August 5.

### POCs (Production Non-Login Accounts)

*   **Email-Only POCs:** You may request accounts for individuals who need to receive CCADB system emails and notifications but do not need to log in to the CCADB interface. These are called **Points of Contact (POCs)**.
*   **No Account Limit:** There is no limit on the number of email-only POC accounts a CA Owner can have.
*   **Use Group Aliases for Broad Communication:** While you can add multiple individual POCs, CA Owners should use the **CA Email Alias 1** and **CA Email Alias 2** fields in the CCADB for communications intended for a group or department.

### API Credentials

*   **One Account Per CA Owner:** Access to the production CCADB API (e.g., for [automated intermediate certificate updates](https://github.com/mozilla/CCADB-Tools/tree/master/API_AddUpdateIntermediateCert)) is limited to **one API account per CA Owner**.
*   **License Consumption:** Authentication to the production environment via the API consumes a license and counts towards your *daily-unique-login* limit.

### Sandbox Environment Accounts

*   **Testing and Integration:** All API testing and integration development must be performed in the CCADB Sandbox environment to avoid consuming production licenses.
*   **Minimize Sandbox Administration:** While there is no hard limit on the number of Primary POC login accounts in the Sandbox environment, CA Owners are requested to minimize account creation to help reduce administrative overhead.
*   **Contact CCADB Support to have sandbox accounts created or managed.**

We welcome you to add your ideas to [CCADB Public](https://groups.google.com/a/ccadb.org/g/public) about the information that you would like the CCADB to provide without requiring a login and how you would like to obtain that information.
