# Incidents
Incidents can happen. Things do not always go as planned, and that can be okay. However, when incidents occur, the underlying issue (i.e., root cause) should be identified and remediated to discourage the incident from occurring again. Formally documenting the incident in a report encourages an understanding of all contributing root cause(s), and it presents the opportunity to clearly communicate a remediation plan to reduce the probability of its reoccurrence. 

Depending on the root programs in which a CA Owner participates, it may be required to:
* create [Audit Incident Reports](incident-report#audit-incident-reports) when audits have non-conformities, qualifications, or modified opinions.
* create [Incident Reports](incident-report#incident-reports) for all other incidents.

These reports provide lessons learned and transparency about the steps the CA Owner takes to address the immediate issue and prevent future issues. If the underlying problem goes unfixed, then other issues that share the same root cause will subsequently surface. Additionally, incident reports help the Web PKI ecosystem as a whole because they promote continuous improvement, information sharing, and highlight opportunities to define and adopt improved practices, policies, and controls.

|Version|Effective Date|
|-|-|
|2.0 (current)|October 17, 2023| 
|[1.0](https://github.com/mozilla/www.ccadb.org/blob/master/incident_archive/ir_version_1_0.md)|February 15, 2023|

## Incident Reports

The purpose of incident reporting is to help us work together to build a more secure web. Therefore, the incident report should share lessons learned that could be helpful to all CA Owners in building better systems. The incident report should explain how systems or processes failed, how the mis-issuance or incident was made possible, and why the problem was not detected earlier. In addition to the timeline of responding to and resolving the incident, the incident report should explain how the CA Owner's systems or processes will be made more robust, and how others may learn from the incident.

Each incident should result in a report written as soon as the problem is fully diagnosed and (temporary or permanent) measures have been put in place to ensure it will not reoccur. If the permanent fix will take significant time to implement, you should not wait until this is done before issuing the report.

An initial report should be filed within 72 hours of the CA Owner being made aware of the incident. If a full incident report is not yet ready, CA Owners should provide a preliminary report containing an executive summary of the incident and a date by which the full report will be posted. The full incident report must be posted within two weeks of the incident. Once the report is posted, CA Owners should respond promptly to questions that are asked, and in no circumstances should a question linger without a response for more than one week, even if the response is only to acknowledge the question and provide a later date when an answer will be delivered. 

There should be a single incident report for each distinct matter, and CA Owners should submit an additional, separate incident report when:

- Policy requires the revocation of one or more certificates by a certain deadline, such as those in BR section 4.9, but that deadline will not be or has not been met by the CA Owner.
- In the process of researching one incident, another incident with a distinct root cause and/or remediation is discovered.
- After an incident is marked resolved in Bugzilla, the incident reoccurs.

The incident report may well repeat things previously said in discussions or Bugzilla comments. This is entirely expected. The report should be a summary of previous findings. The existence of data in discussions or Bugzilla comments does not excuse a CA Owner from the task of compiling a proper incident report.

Open incident reports should be updated:

- on or before the "Next update" date in the "Whiteboard" field of the bug;
- weekly, if a "Next update" date is not recorded; or
- when Action Items are changed, completed, or delayed.

### Creating an Incident Report

Create a new Bugzilla issue by filling out the Summary and Description fields of [this form](https://bugzilla.mozilla.org/enter_bug.cgi?format=__default__&product=CA%20Program&component=CA%20Certificate%20Compliance&bug_type=task). The Summary field in Bugzilla (aka Subject line) should begin with the CA Owner's name, followed by a colon, and a brief title that highlights the type of incident being reported. The Description field may contain the full incident report (copied and pasted from the markdown template, as explained below). If a Bugzilla issue has already been created for this incident (e.g. by an external security researcher) you may skip this step.

To create the full incident report, copy the markdown template below and fill out each section according to the following instructions and requirements:

1. The Summary section (as set forth in the markdown template below) should contain a short description of the nature of the issue. This provides just enough context for new readers to understand the details in the rest of the report.
2. The Impact section should contain a short description of the size and nature of the incident. For example: how many certificates, OCSP responses, or CRLs were affected; whether the affected objects share features (such as issuance time, signature algorithm, or validation type); and whether the CA Owner had to cease issuance during the incident.
3. The Timeline section must include a detailed timeline of all events and actions leading up to and taken during and after the incident. The timeline must include not just the actual discovery of the incident and subsequent events, but also relevant events occuring beforehand (e.g. something changed or was introduced). All times should be in UTC (or local system time with the offset from UTC provided) and have at least minute-level granularity. In addition, it must indicate the following events:
   - All policy, process, and software changes that contributed to the Root Cause
   - The time at which the incident began
   - The time at which the CA Owner became aware of the incident
   - The time at which the incident ended
   - The times at which issuance ceased and resumed, if relevant
4. The Root Cause Analysis section must contain a detailed analysis of the conditions which combined to give rise to the issue. It is unusual for an incident to have a single root cause; often there must be a confluence of several issues such as a software bug, insufficient checks, and a malformed request. Make sure that all contributing causes are identified and described, including noting when they first arose and how they avoided detection until they were discovered or identified.
5. The Lessons Learned section should contain the following subsections:
   - What went well: a list of things that caused the incident to have less impact than it otherwise could have, such as early detection, rapid response, or good safety mechanisms. This section provides an opportunity for others to learn from the good practices of this CA Owner.
   - What didn't go well: a list of things that caused the incident to have more impact than it otherwise would have, such as missing checks or unclear documentation. Each item here must have at least one corresponding Action Item below and should provide opportunities for others to ensure they make similar improvements if they haven't already.
   - Where we got lucky: a list of things that went well, but which cannot be relied upon, such as early detection by an external security researcher or limited impact simply due to a small number of requests. Items here should generally also have corresponding Action Items, so that the CA Owner doesn't have to rely on luck in the future.
6. The Action Items section must contain a list of remediation items that will be undertaken to ensure that similar incidents do not reoccur in the future. Note that it is not sufficient for these action items to simply stop this incident, they must create additional protections to prevent future incidents. Each Action Item should state:
   - A short description of the action to be taken.
   - A classification of whether the action will help _Prevent_ future incidents, _Mitigate_ the impact of future incidents, or _Detect_ future incidents. CA Owners are encouraged to propose action items in all three categories, with an emphasis on prevention and mitigation.
   - A date by which the action item will be complete.
7. The Appendix is for all supporting data: log files, graphs and charts, etc. In particular, in the case of incidents which directly impacted certificates, the Appendix must include a listing of the complete certificate details of all affected certificates. The recommended format is to ensure that all affected certificates are logged to CT, then to attach a text file where each line is of the form `https://crt.sh/?sha256=[sha256 fingerprint of the certificate]`. When the incident being reported involves an SMIME certificate, if disclosure of personally identifiable information in the certificate may be contrary to applicable law, please provide at least the certificate serial number and SHA256 hash of the certificate.

### Incident Report Template

```markdown
## Incident Report

### Summary



### Impact



### Timeline

All times are UTC.

YYYY-MM-DD:
- HH:MM Example

### Root Cause Analysis



### Lessons Learned

#### What went well

* 

#### What didn't go well

* 

#### Where we got lucky

* 

### Action Items

| Action Item | Kind | Due Date |
| ----------- | ---- | -------- |
| Example | Prevent | 2038-01-19 |

### Appendix

#### Details of affected certificates

```

### Example Incident Reports

Here are some examples of good practice, where a CA Owner did most or all of the things recommended above:

- [Failure to provide OCSP Responses for some certificates](https://bugzilla.mozilla.org/show_bug.cgi?id=1753123)
- [Incorrect OCSP responses](https://bugzilla.mozilla.org/show_bug.cgi?id=1763203)

Note that these incident reports conformed to an earlier version of the incident reporting template.

## Audit Incident Reports ##

When audits are performed, an audit statement may document qualifications or non-conformities (i.e., findings) that were identified during the audit. In some cases, each finding may have been self-reported by a CA Owner or external third-party in a previous incident report. In cases where each finding was not previously recorded in an incident report create a new Bugzilla issue by filling out the Summary and Description fields of [this form](https://bugzilla.mozilla.org/enter_bug.cgi?format=__default__&product=CA%20Program&component=CA%20Certificate%20Compliance&bug_type=task). The Summary field should include the CA Owner name, a colon, and "Findings in 20XX Audit", where XX is the year the audit period or point-in-time ended (e.g., CA ABC: Findings in 2023 Audit).

To create the full audit incident report, copy the markdown template below and fill out each section according to the following instructions and requirements:

1. The Finding section should contain a short description of the nature of each finding. This provides context for the reader to understand the nature of the non-compliance identified by the Auditor.
2. The Root Cause Analysis section must contain a detailed analysis of the conditions which combined to give rise to the issue. It is unusual for an incident to have a single root cause; often there must be a confluence of several issues such as a software bug, insufficient checks, and a malformed request. Make sure that all contributing causes are identified and described, including noting when they first arose and how they avoided detection until they were discovered or identified.
3. The Action Items section must contain a list of remediation items that were or will be undertaken to ensure that similar incidents do not reoccur in the future. Note that it is not sufficient for these action items to simply stop this incident, they must create additional protections to prevent future incidents. Each Action Item should state:
   - A short description of the action that was or will be taken.
   - A classification of whether the action will help _Prevent_ future incidents, _Mitigate_ the impact of future incidents, or _Detect_ future incidents. CA Owners are encouraged to propose action items in all three categories, with an emphasis on prevention and mitigation.
   - A date by which the action item was or will be completed.

If the audit includes multiple findings, the audit incident report should include a separate Finding, Root Cause Analysis, and Action Items section for each finding. 

### Audit Incident Report Template

```markdown
## Audit Incident Report

### Finding #1



### Root Cause Analysis



### Action Items

| Action Item | Kind | Due Date |
| ----------- | ---- | -------- |
| Example | Prevent | 2038-01-19 |

### Finding #2



### Root Cause Analysis



### Action Items

| Action Item | Kind | Due Date |
| ----------- | ---- | -------- |
| Example | Prevent | 2038-01-19 |

```
