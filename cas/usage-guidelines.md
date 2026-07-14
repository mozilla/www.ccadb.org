# CCADB Usage Guidelines #

This page is intended for CA Owners who have requested and obtained access to the CCADB. We look forward to your help in keeping your CA’s data up-to-date in the CCADB, and ask that you follow these usage guidelines.

## CCADB Accounts and Logins

The CCADB supports different types of accounts to facilitate management and communication while optimizing license usage.

### Primary POCs (Production Login Accounts)

Each CA Owner should:

*   **Designate a Primary Login:** Identify one individual who usually logs into the CCADB on the CA’s behalf. An individual with login credentials is referred to as a **Primary Point of Contact (Primary POC)**.
*   **Limit Backup Logins:** Designate backup individuals who can log in when the primary contact is unavailable. To manage license costs, **each CA Owner is limited to a maximum of 5 Primary POC (login) accounts**.
*   **Manage Login Frequency:** Limit usage to less than 5 *daily-unique-logins* per month on average (approximately once per week). We understand some months require more activity to update data, which is why we monitor average usage.

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
