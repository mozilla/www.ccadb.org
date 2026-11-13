# Managing Points of Contact

CA Owners use an **Add/Update Contacts** case in the CCADB to add new individual Points of Contact (POCs), update existing contact details or CCADB login permissions, mark departing contacts as obsolete, or reactivate previously obsolete contacts.

Like CA Owner and root certificate updates, contact changes are **staged in a case** and take effect only after a Primary POC clicks **Submit to Root Store** and a Root Store Operator reviews and syncs the case. Multiple contact additions, edits, deactivations, and reactivations can be combined in a single **Add/Update Contacts** case.

> **Using the Right Workflow:**
> - **Individual contacts (`Primary POC` and `POC`):** Submit an **Add/Update Contacts** case (instructions on this page).
> - **Non-personal group email aliases (`CA Email Alias 1` and `CA Email Alias 2`):** Submit an **Add/Update Root Request** case on the **CA OWNER** tab; see [Managing CA Owner and Root Certificate Records](updates#ca-owner).
> - **New CA organizations without CCADB access yet:** Submit the initial [Application for CCADB Access](request-access#application-for-ccadb-access).

## Contact Types and Requirements

Per [CCADB Policy Section 2](../policy#2-contact-information-disclosures), every CA Owner must maintain **at least one Primary POC**, **at least one additional POC** (who may also be a Primary POC; designating a backup Primary POC is strongly recommended), and **at least one non-personal group email alias**.

CCADB automatically sets each individual contact's **Type** based on how you answer `Is a CCADB Login Required?` and `Is this Contact Obsolete?`:

| Contact Type | Login & Notification Access | Key Field & License Rules |
|---|---|---|
| **Primary POC** | **Can log in** to the CCADB to manage records and cases, and **receives** CCADB notifications. Should be authorized to speak for and enter into binding commitments on behalf of the CA. | • Triggered when `Is a CCADB Login Required?` = `Yes`.<br>• Requires **Name**, **CA Owner-affiliated Email**, and **Phone Number**.<br>• Requires **Bugzilla Username** if the contact holds a Bugzilla account for responding to [Incident Reports](incident-report).<br>• **Maximum of 5 Primary POCs per CA Owner** (each consumes a CCADB license; see [Usage Guidelines](usage-guidelines)). Requesting more than 5 requires written justification in the case. |
| **POC** | **Cannot log in** to the CCADB, but **receives** CCADB system notifications and security/audit communications. | • Triggered when `Is a CCADB Login Required?` = `No` and `Is this Contact Obsolete?` = `No`.<br>• Requires **Name** and **CA Owner-affiliated Email** (plus **Bugzilla Username** if applicable).<br>• **No limit** on the number of email-only POCs. |
| **Obsolete** | **No login access** and **no notifications**. Listed at the bottom of your organization's POC list prefixed with `**`. | • Triggered once `Is this Contact Obsolete?` = `Yes` (with `Is a CCADB Login Required?` = `No`) is synced by a Root Store Operator.<br>• Frees up a Primary POC license if the contact previously had login access. |

## Table of Contents

1. [Creating an Add/Update Contacts Case](#1-creating-an-addupdate-contacts-case)
2. [Managing Contacts Within Your Case](#2-managing-contacts-within-your-case)
   - [Adding a New Contact](#adding-a-new-contact)
   - [Updating an Existing Contact (Including Name or Email Changes)](#updating-an-existing-contact-including-name-or-email-changes)
   - [Removing a Contact (Marking as Obsolete)](#removing-a-contact-marking-as-obsolete)
   - [Reactivating a Previously Obsolete Contact](#reactivating-a-previously-obsolete-contact)
3. [Submitting Your Case and Stopping All Communications](#3-submitting-your-case-and-stopping-all-communications)

---

## 1. Creating an Add/Update Contacts Case

1. [Log in to the CCADB](https://ccadb.my.site.com/CustomLogin) as an existing **Primary POC** (see [Getting Started](getting-started) if needed).
2. Click the **My CA** tab in the top navigation bar.
3. Click the **CASES** sub-tab under your CA Owner's name near the upper-left corner.
4. Click the **New** button on the right side of the page (below **Get URLs**).
5. Select **Add/Update Contacts** and click **Next**.
6. Enter a descriptive **Subject** for your case (for example, `Update Points of Contact for <CA Name>` or `Add Primary POC and Remove Departing Contact for <CA Name>`).
7. Click **Save**.
8. Open your newly created case using any of the following methods:
   - Click the case number in the green confirmation banner across the top of the page (`Case ###### was created`).
   - Return to **My CA** → **CASES** and click the case number in the top row of the **Case** column.
   - Go to your CCADB **Home** page, expand **Open Add/Update Contacts Cases** (or **Open Cases**) under **CA Task List**, and click the case number.

Inside the case, all contacts for your organization are displayed in an expandable alphabetical list. **Obsolete** contacts appear at the bottom of the list with **`**`** in front of their name. Whenever you save an addition or edit within the case, a green banner confirms the update and any modified values appear in **bold blue text**.

---

## 2. Managing Contacts Within Your Case

You can perform one or multiple contact updates in the same **Add/Update Contacts** case before clicking **Submit to Root Store**.

### Adding a New Contact
1. Click the **Add Contact** button inside the case.
2. Complete all mandatory fields marked with an asterisk (**`*`**):
   - Set **`Is a CCADB Login Required?`** to **`Yes`** for a **Primary POC** (phone number required; counts toward the 5-license limit, so include a justification if exceeding 5) or **`No`** for an email-only **POC**.
   - Enter the contact's **Bugzilla Username** if they have a Bugzilla account used to respond to [Incident Reports](incident-report).
3. Click **Save**. The new contact appears expanded in your POC list with proposed values highlighted in **bold blue text**.

### Updating an Existing Contact (Including Name or Email Changes)
1. Locate the contact in the alphabetical list and click their section header to expand their details.
2. Click the **pencil icon** on a field (or click the downward arrow **`▼`** on the section header) to enter edit mode, noting any mandatory fields required for that contact's **Type**.
3. Enter your updates and click **Save**.

> **Note on Changing a Primary POC's Name or Email Address:** A Primary POC may update their own (or a colleague's) name or email address in an **Add/Update Contacts** case. Name or email changes for login accounts may require additional background correlation by Root Store Operators during review; once processed, a Primary POC whose email address changed will receive new login instructions at their updated email address.

### Removing a Contact (Marking as Obsolete)
When a colleague leaves your organization or no longer handles CCADB responsibilities, mark them as obsolete promptly (you can also audit stale contacts anytime via the **Contacts who may be obsolete** report on your CCADB **Home** page):

1. Find the contact in the list, click their section header to expand their record, and click the **pencil icon** (or section header **`▼`**).
2. Change **`Is this Contact Obsolete?`** to **`Yes`**.
3. If **`Is a CCADB Login Required?`** is currently **`Yes`**, change it to **`No`**.
4. Click **Save**. Once the case is processed by a Root Store Operator, the contact's **Type** changes to **Obsolete** (moving them to the bottom of the list with **`**`**) and any Primary POC license they held becomes available for your CA Owner.

### Reactivating a Previously Obsolete Contact
If a previously obsolete colleague returns to CCADB duties:

1. Scroll to the bottom of the contacts list, expand the **`**`** contact's section header, and click the **pencil icon** (or section header **`▼`**).
2. Change **`Is this Contact Obsolete?`** to **`No`**.
3. If the contact requires CCADB login access, set **`Is a CCADB Login Required?`** to **`Yes`** (and verify that all mandatory Primary POC fields, such as phone number, are populated).
4. Click **Save**.

---

## 3. Submitting Your Case and Stopping All Communications

### Submitting to Root Store Operators
1. Confirm all warnings and validation errors in the case are resolved, then click **Submit to Root Store** in the upper-right corner of the page.
2. The Root Store Operator on rotation will review and sync your changes to the CCADB (or return the case with comments if clarification is needed).
3. Once synced, any newly added or reactivated **Primary POC** (or Primary POC with an updated email address) automatically receives an email with instructions to log in to the CCADB.

### Stopping All CCADB Communications
If a CA Owner no longer participates in the CCADB and wants to stop receiving **all** system communications, a Primary POC can log in and submit two cases:

1. Submit an **Add/Update Contacts** case setting **`Is this Contact Obsolete?`** to **`Yes`** (and **`Is a CCADB Login Required?`** to **`No`**) for every **Primary POC** and **POC**.
2. Submit an **[Add/Update Root Request](updates#ca-owner)** case and clear the values for **`CA Email Alias 1`** and **`CA Email Alias 2`** on the **CA OWNER** tab.

Once a Root Store Operator reviews and syncs both cases to the CCADB, all automated system emails to the organization will stop.
