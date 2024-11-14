# Audit Incident Reporting Guidelines

## Change History

|Version|Effective Date|
|-|-|
|2.1 (current)|TBD| 
|[2.0](https://github.com/mozilla/www.ccadb.org/blob/master/incident_archive/ir_version_2_0.md)|October 17, 2023| 
|[1.0](https://github.com/mozilla/www.ccadb.org/blob/master/incident_archive/ir_version_1_0.md)|February 15, 2023|

## Audit Incident Reporting

**Note:** The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" on this page are to be interpreted as described in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

When audits are performed, an audit statement may document qualifications or non-conformities (i.e., findings) that were identified during the audit. In some cases, each finding disclosed in the audit statement may have been self-reported by a CA Owner or third party in a previous [Incident Report](incident-report). In cases where **each** finding was *not* previously recorded in an Incident Report, CA Owners MUST create a new Bugzilla issue by filling out the "Summary" and "Description" fields of [this form](https://bugzilla.mozilla.org/enter_bug.cgi?format=__default__&product=CA%20Program&component=CA%20Certificate%20Compliance&bug_type=task). The Summary field MUST include the CA Owner name, a colon, and "Findings in 20XX Audit", where XX is the year the audit period or point-in-time ended (e.g., "CA ABC: Findings in 2023 Audit").

To create the audit incident report, copy the Markdown template below and fill out each section according to the following instructions and requirements.

If the audit includes multiple findings, the audit incident report MUST include a separate Finding, Root Cause Analysis, and Action Items Sections for each finding. 

### Audit Incident Report Template

```markdown

## Audit Incident Report

### Finding # (i.e., #1)
<!---

**Expectations:**

- This section MUST contain a description of the nature of each finding. This provides context for the reader to understand the nature of the non-compliance identified by the Auditor.

-->

#### Root Cause Analysis
<!---

**Expectations:**

- A root cause is defined as a factor that caused a nonconformance and SHOULD be permanently eliminated through process improvement.
- This section MUST contain a detailed analysis of the conditions which combined to give rise to the issue.
- It is unusual for an incident to have a single root cause; often there is a confluence of several issues such as a software bug, insufficient checks, and a malformed request.
- Make sure that all contributing causes are identified and described, including noting when they first arose and how they avoided detection until they were discovered or identified. 

##### Issue [#]: [Title]
- **Description:** [A detailed description of the specific issue.]
- **Issue Onset:** [Date when the issue began.]
- **Issue Detection:** [Date when the issue was detected or otherwise made known.]
- **Issue Resolution:** [Actual or planned date when the issue will be considered resolved.]
- **Symptoms that Led to Detection**: [A detailed description of the circumstances that led to the detection of the issue.]
- **How the Issue Avoided Detection**: [A detailed description of how the issue was not detected earlier.]
- **Root Cause Analysis Methodology Used**([OPTIONAL, but RECOMMENDED]): [A description of the methodology used to derive the issue described above (e.g., "5-Whys", Fishbone Diagram, Pareto Analysis, etc.)]

-->


#### Action Items
<!---

**Expectations:**

- This section MUST contain a list of remediation items that will be undertaken to ensure that similar incidents do not reoccur in the future.
- Note that it is not sufficient for these action items to simply stop this incident, they MUST create additional protections to prevent future incidents.
- Each Action Item MUST state:
     - **Action Item Description** [A detailed description of the action to be taken.]
     - **Kind** [A classification of whether the action will help Prevent future incidents, Mitigate the impact of future incidents, or Detect future incidents. CA Owners are encouraged to propose action items in all three categories, with an emphasis on Prevent and Mitigate.] 
     - **Corresponding Root Cause(s)** [The specific Root Cause that the Action intends to remediate (i.e., each issue entry in the "Root Cause Analysis" and "What didn't go well" Sections MUST be mapped to at least one specific action item)]
     - **Due Date** [A date by which the action item will be complete.]

| Action Item | Kind    | Corresponding Root Cause(s) | Due Date   |
| ----------- | ----    | --------------------------- | ---------- |
| Example     | Prevent | Root Cause # 1              | 2025-01-19 |

-->

```


### Are there examples of “good" Incident Reports?

Here are some examples of good practice, where a CA Owner did most or all of the things recommended above:

- [QuoVadis: Findings in 2024 ETSI Audit of QuoVadis Qualified Web ICA G2](https://bugzilla.mozilla.org/show_bug.cgi?id=1918467)
     - Clear "Summary" statement and finding descriptions allow readers to quickly understand the scope of the incident.
     - Detailed set of "Action Items" with accompanying background help the reader understand the steps taken to meaningfully reduce the liklihood of the issues repeating.

Upon adoption of the updated Incident Report templates above, examples of good practice will be updated.
