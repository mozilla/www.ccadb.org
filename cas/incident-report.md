# Incident Reporting Guidelines

## Change History

|Version|Effective Date|
|-|-|
|3.1 (current)|June  15, 2025| 
|[3.0](https://github.com/mozilla/www.ccadb.org/blob/master/incident_archive/ir_version_3_0.md)|March 1, 2025| 
|[2.0](https://github.com/mozilla/www.ccadb.org/blob/master/incident_archive/ir_version_2_0.md)|October 17, 2023| 
|[1.0](https://github.com/mozilla/www.ccadb.org/blob/master/incident_archive/ir_version_1_0.md)|February 15, 2023|

## Incident Reporting

Systems, processes, and people aren't perfect. Omissions and deviations from expected outcomes can sometimes happen. However, when omissions or deviations are discovered, the underlying issues (i.e., root causes) need to be identified and remediated to discourage future recurrence. Formally documenting these cases, in the form of an Incident Report, promotes a thorough understanding of contributing factors and facilitates clear communication of remediation plans, while also fostering a culture of continuous improvement within the Web PKI ecosystem.

This page describes the CCADB Incident Reporting Framework and corresponding guidelines. For questions, contact support [at] ccadb [dot] org.

### Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" on this page are to be interpreted as described in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

Unless otherwise stated, "certificate" on this page refers to a final certificate, distinct from a precertificate (as described in [RFC 6962](https://datatracker.ietf.org/doc/html/rfc6962)).

## Table of Contents

[**Useful background**](#useful-background)
- [What is considered an incident?](#what-is-considered-an-incident)
- [What is considered an audit finding?](#what-is-considered-an-audit-finding)
- [Why is public reporting important?](#why-is-public-reporting-important)
- [What are the key characteristics of these reports?](#what-are-the-key-characteristics-of-these-reports)
- [What does root cause analysis consider?](#what-does-root-cause-analysis-consider)

[**Community participation in the reporting process**](#community-participation-in-the-reporting-process)
- [Who can submit an Incident Report?](#who-can-submit-an-incident-report)
- [Are there other ways to become involved in the reporting process?](#are-there-other-ways-to-become-involved-in-the-reporting-process)
- [What Bugzilla account can I use?](#what-bugzilla-account-can-i-use)

[**Report lifecycle management**](#report-lifecycle-management)
- [How do I submit a report?](#how-do-i-submit-a-report)
- [How do I submit a security-sensitive incident report?](#how-do-i-submit-a-security-sensitive-incident-report)
- [How are reports scoped?](#how-are-reports-scoped)
- [What format is used?](#what-format-is-used)
- [When are reports expected?](#when-are-reports-expected)
- [When are reports updated?](#when-are-reports-updated)
- [How are reports closed?](#how-are-reports-closed)
  
[**Report templates**](#report-templates)
- [Preliminary Incident Report Template](#preliminary-incident-report)
- [Full Incident Report Template](#full-incident-report)
- [Report Closure Template](#closure-report)

[**Report field definitions and expectations**](#report-field-definitions-and-expectations)
- [Incident Reports](#incident-reports)
- [Incident Closure Summary](#incident-closure-summary)

[**Illustrative practices**](#illustrative-practices)
- [Are there examples of "good" practices?](#are-there-examples-of-good-practices)
- [Are there examples of "bad" practices?](#are-there-examples-of-bad-practices)
- [Are there examples of "good" reports?](#are-there-examples-of-good-reports)


### Useful background

#### What is considered an incident?

Minimally, a failure to meet the commitments described in any of the following policies is considered an incident:
- a CA Owner's own policies (e.g., CP, CPS, or combined CP/CPS);
- applicable requirements promulgated by the CA/Browser Forum;
- the CCADB Policy; or
- any applicable Root Store Operator policy.

Root Store Operator policies may further define what those individual programs consider incidents and/or outline additional incident reporting expectations.

It's important to note that the existence of an Incident Report does not generally indicate serious problems with a CA. 

For publicly-trusted CA Owners, the number of incident reports filed in Bugzilla is less important than the content and quality of those reports.

#### What is considered an audit finding?

Qualifications, non-conformities, and other deviations or omissions identified during audits are considered "findings."

These items are commonly, but not exclusively, presented as either:
- major non-conformities,
- minor non-conformities,
- qualifications,
- qualified opinions, or
- other matters.

#### Why is public reporting important?

Incident Reports provide lessons learned and transparency about the steps the CA Owner takes to address the immediate issue and prevent future issues. If the underlying problem goes unfixed, then other issues that share the same root cause will subsequently surface. 

The public reporting process is important because it promotes continuous improvement, information sharing, and highlights opportunities to define and adopt improved practices, policies, and controls. Further, public reporting helps convey the implications and impact of an event so that affected stakeholders have an opportunity to assess risk and determine if it warrants further action. Together, these activities help build a more secure web. 

#### What are the key characteristics of these reports?

Reports are expected to:
- be candid (i.e., focusing on honesty and forthrightness, even when revealing uncomfortable truths), timely (i.e., released without undue delay), and transparent (i.e., emphasizing open accessibility of information);
- clearly (i.e., avoiding jargon, defining technical terms, adding useful background information) and objectively (i.e., supporting claims with data) communicate the scope, impact, and severity of an incident;
- help community members understand the relevant architectures, implementations, operations, and external dependencies surrounding an incident;
- demonstrate a detailed understanding of the root cause(s) of an incident;
- unambiguously explain how systems, processes, and/or policies failed; 
- describe the circumstances that prevented the problem(s) from being detected earlier;
- describe a clear timeline of a CA Owner's actions while responding to and remediating an incident;
- include a detailed and measurable explanation of actions taken or planned by the CA Owner that demonstrate a substantive commitment of how the CA Owner's systems, policies, and/or processes will be made more robust (i.e., demonstrate continuous improvement); and
- share lessons learned that could be helpful to all CA Owners in building better systems policies, and/or processes.

#### What does Root Cause Analysis consider?

Effective Root Cause Analysis (RCA) minimally considers the following points:

1. **Focus on the "why," not just the "what"**. RCAs go beyond identifying what went wrong and delve deeper into why it happened. This often involves looking past the immediate technical or policy failure and considers contributing factors like human error, process deficiencies, or system design flaws.

2. **Use a systematic approach**. Employ structured methodologies like the following approaches to help ensure a thorough and organized investigation:
   - [**Chesterton’s Fence**](https://fs.blog/chestertons-fence/): Before changing anything, understand why it's there. This helps avoid unintended consequences and ensures solutions address the root cause, not just symptoms.
   - [**5 Whys**](https://en.wikipedia.org/wiki/Five_whys): Repeatedly ask "why" as many times as necessary to uncover the underlying cause of a problem. This simple technique helps drill down to the core issue and prevents superficial solutions.
   - **Multi/Second Order Thinking** ([1](https://fs.blog/second-order-thinking/), [2](https://betterletter.substack.com/p/second-order-thinking), [3](https://medium.com/@noahmp/second-order-thinking-3fc2a224b131)): Think beyond immediate consequences. Consider the ripple effects of actions and potential downstream impacts to make more informed decisions.
   - [**CATWOE**](https://www.toolshero.com/problem-solving/catwoe-analysis/): Analyze a problem from different perspectives (customers, actors, transformation, world view, owner, environmental constraints). This ensures a holistic understanding of the issue and its context.
   - [**Cause and Effect / Fishbone or Ishikawa**](https://en.wikipedia.org/wiki/Ishikawa_diagram): Visually map potential causes of a problem, categorizing them to identify root causes and relationships. This promotes systematic exploration and prevents overlooking factors.
   - [**Drilling Down**](https://sigma.software/about/media/problem-solving-techniques-part-two#2.-drill-down): Break complex problems into smaller, more manageable parts. This allows for focused investigation and helps identify specific areas for improvement.
   - **SRE Handbook Guidance**: These chapters provide practical advice on managing incidents effectively, including communication, coordination, and postmortem analysis. They emphasize a blameless culture focused on learning and improvement.
       - [Chapter 14](https://sre.google/sre-book/managing-incidents/)
       - [Chapter 15](https://sre.google/sre-book/postmortem-culture/)

4. **Consider all potential contributing factors**. RCAs consider a broad range of potential causes, including technical issues, policy issues, human factors, process breakdowns, and external influences. It's crucial to avoid jumping to conclusions or focusing solely on the most obvious cause(s).

5. **Collect and analyze data**. Data is critical for supporting RCA conclusions and may include reviewing logs, monitoring metrics, internal incident reports, and other relevant information to identify patterns and anomalies.

6. **Involve relevant stakeholders**. RCAs are a collaborative effort involving engineers, operators, support teams, and other relevant stakeholders to ensure a diverse range of perspectives and expertise is considered.

7. **Prioritize action items**. The ultimate goal of an RCA is to prevent future incidents caused by the same failures; therefore, it's important to identify and prioritize actionable recommendations that address the identified root causes.

8. **Focus on blameless postmortems**. Emphasize a blameless culture when conducting postmortems. The focus is on learning from the incident and improving systems, not on assigning blame or punishing individuals.

9. **Continuously improve the process**. RCA is an iterative process where an organization continuously refines its approach based on lessons learned from previous incidents and evolving best practices.

### Community participation in the reporting process

#### Who can submit an Incident Report?

Anyone should feel encouraged to submit an Incident Report that’s founded upon credible and well-substantiated evidence.

Some Root Store Operator policies require CA Owners to submit an Incident Report as described on this page after self-discovering or being made aware of an Incident (e.g., receiving and corroborating an issue described in a [Certificate Problem Report](https://cabforum.org/working-groups/server/baseline-requirements/requirements/#161-definitions)).
  
#### Are there other ways to become involved in the reporting process?

Absolutely! There are many ways to participate in the incident reporting process beyond submitting new reports. Everyone is encouraged to actively contribute by commenting on existing reports and engaging in constructive discussions. This can include, but is not limited to:
- providing additional information,
- asking clarifying questions,
- discussing technical aspects of the incident,
- suggesting corrective actions,
- highlighting opportunities for improvement,
- contributing lints to open source linting projects to promote improved future issue detection/prevention, and
- sharing lessons learned from past experiences.

Individuals representing CA Owners are especially encouraged to participate broadly in the reporting processes, extending their contributions beyond incidents involving only their own organization. Sharing insights and perspectives across organizational boundaries fosters a collaborative learning environment and strengthens the overall security posture of the Web PKI ecosystem.

Please keep all comments constructive, relevant, and in line with the [CCADB Code of Conduct](https://docs.google.com/document/d/19ALqEvHtTE6OUTz2FaOXrU9gruIdvia5EDh3hXeGpZA/edit#heading=h.cumc0pgd1s7c) to ensure productive dialogue.

#### What Bugzilla account can I use?

**For individuals affiliated with a Publicly-Trusted CA Owner:**
- **To better encourage blamelessness**, when posting incident reports or responding to comments on reports for which they are affiliated, participants MAY respond from a Bugzilla account associated with one of the CA e-mail aliases disclosed to the CCADB, rather than an individual contributor’s account.
- **To better respect a desire for individual privacy and potential risk of retaliation**, individuals participating in the reporting process MAY participate **responsibly** from an account that does not identify the individual posting or their organizational affiliation.

**For everyone else:** Create a new Bugzilla account following [these](https://bugzilla.mozilla.org/createaccount.cgi) instructions. 

**Remember**, please keep all comments constructive, relevant to the corresponding report, and in line with the [CCADB Code of Conduct](https://docs.google.com/document/d/19ALqEvHtTE6OUTz2FaOXrU9gruIdvia5EDh3hXeGpZA/edit#heading=h.cumc0pgd1s7c).

### Report lifecycle management

#### How do I submit a report?

Create a new Bugzilla issue by filling out [this form](https://bugzilla.mozilla.org/enter_bug.cgi?format=__default__&product=CA%20Program&component=CA%20Certificate%20Compliance&bug_type=task). 

- The "Summary" field in Bugzilla (i.e., "Subject line") MUST begin with the CA Owner’s name, followed by a colon, and a brief title that highlights the type of incident being reported (e.g., "EXAMPLE CA OWNER: Incorrect Subject RDN Encoding"). The CA Owner's name SHOULD match exactly with the CA Owner value in the CCADB.
- The "Description" field MAY contain a Preliminary or Full Incident Report (copied and pasted from the corresponding Markdown template, as explained [below](#report-templates)).

#### How do I submit a security-sensitive incident report?

For additional context on what might be considered a "security-sensitive" incident, see [here](https://wiki.mozilla.org/CA/Vulnerability_Disclosure).

Sensitive security incidents and vulnerabilities can be reported in Bugzilla by filling out [this form](https://bugzilla.mozilla.org/enter_bug.cgi?bug_type=task&component=CA%20Security%20Vulnerability&groups=ca-program-security&product=CA%20Program). Under the heading "People", be sure to add incident-reporting [at] ccadb [dot] org to the report's CC list.

_**Under the heading "Security", make sure that the "CA Program Security" checkbox is ticked -- leaving all security boxes unchecked makes it a public bug.**_

After opening a security-sensitive incident in Bugzilla, also email incident-reporting [at] ccadb [dot] org.

Following the submission of a security-sensitive incident in Bugzilla, the corresponding CA Owner MUST file a public incident report once they have determined that the associated security risk is closed.

#### How are reports scoped?

There SHOULD be a single Incident Report for each distinct matter, and CA Owners MUST submit an additional, separate Incident Report when:
- policy requires the revocation of one or more certificates by a certain deadline, such as those in BR Section 4.9, but that deadline will not be or has not been met by the CA Owner (i.e., a delayed revocation Incident Report).
- in the process of researching one incident, another incident with a distinct root cause and/or remediation is discovered.
- after an incident is marked resolved in Bugzilla, the incident reoccurs.

All reports MUST be free-standing and not rely on the contents of other reports.  While reports MAY repeat information from discussions or Bugzilla comments, they SHOULD summarize previous findings.  CA Owners are responsible for compiling a complete report according to these guidelines, even if information exists elsewhere.

#### What format is used?

Use one of the templates below, depending on the type of report being disclosed:

- [Preliminary Incident Report](#preliminary-incident-report) (for third party reporters and CA Owners submitting Preliminary Incident Reports)
- [Full Incident Report](#full-incident-report) (for CA Owners submitting Full Incident Reports)

Report content MUST be provided in Markdown (i.e., not in the form of an attachment) and SHOULD utilize Markdown's [formatting features](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) (headers, lists, emphasis, etc.) to ensure clarity and readability. Individuals submitting reports SHOULD use Bugzilla's "preview" feature to confirm rendering appears as expected before posting.

Learn more about expected report content and a description of the fields included in the reporting templates [here](#report-field-definitions-and-expectations).

#### When are reports expected?

Within 72 hours of a CA Owner becoming aware of an incident (i.e., the "initial incident disclosure") or an audit finding not previously disclosed in an Incident Report, the CA Owner MUST either:

- disclose a Preliminary or Full Incident Report; or
- respond to a Preliminary Incident Report previously created for the incident by a third party reporter.

In its initial report (i.e, Preliminary or Full Incident Report) or reply to a third-party report, the CA Owner MUST:

- accurately disclose the impact of the incident (e.g., the corpus of then-known mis-issued certificates); and
- describe whether the incident should be considered contained (e.g., because certificate issuance was stopped) or ongoing.

If the described impact of the incident is later found to be inaccurate, the CA Owner MUST clearly communicate a correction, identifying when each following change was detected, the circumstances that led to the inaccuracy, and how this will be avoided in the future.

While Full Incident Reports SHOULD be posted as soon as possible, they MUST be posted within 14 days of the incident’s initial disclosure.

#### When are reports updated?

CA Owners should respond promptly to comments and questions, and MUST respond within 7 days, even if only to acknowledge the request and provide a timeline for a full response.

Open reports MUST be updated:
- on or before the "Next update" date in the "Whiteboard" field of the bug (note: CA Owners MAY request the "Next update" Whiteboard field be set by a Root Store Operator to align with a specific date related to an open Action Item.);
- within 7 days, if a "Next update" date is not recorded;
- in response to community questions or comments as described above; or
- when Action Items are changed, completed, or delayed.

In the case of Incident Reports with a Whiteboard field of "revocation-delay", reports SHOULD be updated every 3 days and MUST be updated no less frequently than every 7 days to describe a summary of: 
- the number of certificates that have been revoked;
- the number of certificates that have not yet been revoked;
- the number of certificates planned for revocation that have expired; and
- an estimate for when all remaining revocations will be completed.

#### How are reports closed?

When all Action Items are complete and no outstanding comments or questions remain, CA Owners MUST (1) request closure in a Bugzilla comment using the template [below](#incident-closure-summary) and (2) select the "Request information from" checkbox and add incident-reporting [at] ccadb [dot] org. Upon doing so, a final call for comments will be made by a Bugzilla moderator, and the report will be closed accordingly.

### Report Templates

The following templates MUST be used when submitting incident reports or requesting report closures.
- [Preliminary Incident Report Template](#preliminary-incident-report)
- [Full Incident Report Template](#full-incident-report)
- [Closure Report Template](#closure-report)

CA Owners submitting reports MUST complete all applicable fields in the relevant template.  Fields that are not applicable MUST still be included and marked 'N/A'.

Learn more about expected report content and a description of the fields included in the templates [below](#incident-report-field-definitions-and-expectations).

#### Preliminary Incident Report

```markdown
## Preliminary Incident Report

### Summary
- **Incident description:**
- **Relevant policies:** 
- **Source of incident disclosure:** 

```

#### Full Incident Report

```markdown
## Full Incident Report

### Summary

- **CA Owner CCADB unique ID:** 
- **Incident description:** 
- **Timeline summary:**
   - **Non-compliance start date:** 
   - **Non-compliance identified date:** 
   - **Non-compliance end date:** 
- **Relevant policies:** 
- **Source of incident disclosure:** 

### Impact

- **Total number of certificates:**
- **Total number of "remaining valid" certificates:** 
- **Affected certificate types:** 
- **Incident heuristic:** 
- **Was issuance stopped in response to this incident, and why or why not?:** 
- **Analysis:** 
- **Additional considerations:** 

### Timeline

### Related Incidents

| Bug                                | Date                        | Description                                                            |
|------------------------------------|-----------------------------|------------------------------------------------------------------------|
| [Related Bug ID](Related Bug URL)  | Date Related Bug was opened | A description of how the subject Bug is related to the Bug referenced. |

### Root Cause Analysis

**Contributing Factor #: title**
- **Description:** 
- **Timeline:** 
- **Detection:** 
- **Interaction with other factors:** 
- **Root Cause Analysis methodology used:**

### Lessons Learned

- **What went well:** 
- **What didn’t go well:** 
- **Where we got lucky:** 
- **Additional:** 

### Action Items

| Action Item | Kind    | Corresponding Root Cause(s) | Evaluation Criteria | Due Date   | Status |
| ----------- | ----    | --------------------------- | ------------------- | -----------| ------ |
| Example     | Prevent | Root Cause # 1              | Criteria            | 2025-01-19 | Value  |

### Appendix

```

#### Closure Report

```markdown

### Report Closure Summary

- **Incident description:** 
- **Incident Root Cause(s):**  
- **Remediation description:**
- **Commitment summary:**  

All Action Items disclosed in this report have been completed as described, and we request its closure.

```

### Report field definitions and expectations

The following sections are intended to describe expected Incident Report content. All fields are mandatory for the corresponding report type, except when described below.

If submitted by the CA Owner corresponding with the report, all fields included in the relevant template MUST be completed. Fields that are not applicable MUST be included in the report and identified as 'N/A'.

#### Incident Reports

**Summary:** The Summary section contains a short description of the nature of the issue and useful background information. This provides just enough context for readers to understand the details in the rest of the report. 

| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **CA Owner CCADB unique ID*** | The CCADB unique ID value (begins with "A" followed by a six-digit number) corresponding to the CA Owner's "CA Owner/Certificate" record disclosed in the CCADB.  |
| **Incident description** | A short description of the nature of the issue. This provides just enough context for new readers to understand the details of the incident. |
| **Timeline summary*** | Describe (1) when the non-compliance began (2), when the non-compliance was detected, and (3) when the non-compliance ended or is expected to end. |
| **Relevant policies** | Describe the policy name(s), applicable version(s), and corresponding section(s) that result in this problem being diagnosed as an incident. |
| **Source of incident disclosure*** | Choice of "Self Reported", "Third Party Reported", or "Audit". |

*Note*: If notified of an incident by an external, third party reporter, please respect their privacy by *only* disclosing their name if affirmatively approved to do so (e.g., say "we received a report from a community member" instead of explicitly naming individuals). Fields marked with an asterisk (*) are not required in Preliminary Incident Reports if submitted by a third party reporter.

**Impact:** The Impact section contains a description of the size and nature of the incident. For example: how many certificates, OCSP responses, or CRLs were affected; whether the affected objects share features (such as issuance time, signature algorithm, or validation type); and whether the CA Owner had to cease issuance during the incident. 

If certificates are impacted, the Impact section MUST include the following information:  

| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **Total number of certificates** | The total count of all certificates affected by the issue(s) described in this Incident Report, including expired and revoked certificates. |
| **Total number of "remaining valid" certificates** | The total count of certificates affected by the issue(s) described in this Incident Report, minus expired and revoked certificates. Minimally, this set of certificates MUST be disclosed in the Appendix section of this report. |
| **Affected certificate types** |  A summary of the corresponding CA/Browser Forum policy OIDs (i.e., DV, IV, OV, and EV) that appear in the certificates affected by this incident (e.g., "This incident affects DV and OV certificates.”) |
| **Incident heuristic** | **EITHER:** <br><br>**(1)** describe a heuristic that would allow a third party to assemble the full corpus of affected certificates, if not provided in the Appendix (e.g., "Any certificate containing policy OID 1.2.3.4.5.6 and issued between 11/13/2024 and 4/11/2024 is affected by this incident. Certificates that have been revoked or are expired are omitted from the certificate list disclosed in the Appendix.") <br><br> **(2)** clearly explain why this isn't possible (e.g., "This incident affected every certificate issued between 5/25/2023 and 6/15/2024 that relied upon BR Validation Method 3.2.2.4.19. Because the relied upon validation method is not described in a certificate, this heuristic cannot be used by a third party to assemble the full corpus of affected certificates. Certificates that have been revoked or expired have been omitted from the certificate list disclosed in the Appendix.), or <br><br> **(3)** the full corpus of affected certificates are disclosed in the Appendix.|
| **Was issuance stopped in response to this incident, and why or why not?** | Yes/No with explanation (e.g., "Yes. As described in the incident timeline, issuance was stopped after learning of this issue to correct the corresponding certificate profile.") |
| **Analysis** | Required when the Whiteboard field contains ‘revocation-delay’, the factors and rationales behind the decision to delay revocation (including detailed and substantiated explanations of how extensive harm would result to third parties–such as essential public services or widely relied-upon systems–and why the situation is exceptionally rare and unavoidable). |
| **Additional considerations** | This field is optional. Share any additional considerations that might be useful in describing the size and nature of the incident. For example, if the issue affected precertificates and certificates differently, describe how and why in more detail here. |

**Timeline:** The Timeline section includes a detailed timeline of all events and actions leading up to and taken during and after the incident. The timeline MUST include not just the actual discovery of the incident and subsequent events, but also relevant events occurring beforehand (e.g., something changed or was introduced). All times MUST be in UTC or UTC+local offset, and SHOULD have at least minute-level granularity.

Expected Timeline elements:
- All policy, process, and software changes that contributed to the Root Cause(s)
- The time at which the incident began
- The time at which the CA Owner became aware of the incident
- The time at which the CA Owner received a Certificate Problem Report (if applicable)
- The time at which the CA Owner provided a preliminary report on its findings to the entity who filed the Certificate Problem Report (if applicable)
- The time at which the CA Owner provided a preliminary report on its findings to the affected Subscriber(s) (if applicable)
- The time at which the CA Owner concluded and disclosed the scope and impact of the incident
- The time at which the CA Owner updated the scope and impact of the incident (if applicable)
- The time(s) at which the CA Owner is expected to complete revocation of affected certificates (if applicable, but required when Whiteboard field contains ‘revocation-delay’)
- The time(s) at which the CA Owner actually completed revocation of affected certificates (if applicable, but required when Whiteboard field contains ‘revocation-delay’)
- The time at which the incident ended
- The times at which issuance ceased and resumed (if applicable)

**Related Incidents:** The Related Incidents section includes a list of all incidents disclosed to the ['CA Certificate Compliance' Bugzilla Component](https://bugzilla.mozilla.org/buglist.cgi?product=CA%20Program&component=CA%20Certificate%20Compliance&resolution=---) related to this incident that have taken place minimally in the last two (2) years. "Related Incidents" MUST consider incidents beyond those corresponding to the CA Owner subject of this report.

| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **Related Bug ID** | The Bugzilla ID corresponding to the related incident. |
| **Related Bug URL** | The Bugzilla URL corresponding to the related incident. |
| **Opened date** | The date the related incident was opened. |
| **Description** | A description of how the related incident is similar to the subject incident report. |

**Root Causes:** The Root Causes section contains a detailed analysis of the conditions which combined to give rise to the issue. It is unusual for an incident to have a single root cause; often there is a confluence of several issues such as a software bug, insufficient checks, and a malformed request. Make sure that all contributing factors are identified and described, including noting when they first arose and how they avoided detection until they were discovered or identified.

| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **Description** | Describe the specific condition, event, or issue that contributed to the incident. Analyze its role in the incident's development. Consider when this factor first arose and its initial impact.  |
| **Timeline** | Trace the timeline of the contributing factor from its inception to its role in the incident. When was it introduced or created? How did it evolve over time? |
| **Detection** | Describe how the contributing factor was detected, and explain how it avoided detection prior to the incident. Were there inadequate safeguards, missed signals, or other factors that allowed it to persist? |
| **Interaction with other factors** | Analyze how the contributing factor interacted with other identified factors to create the conditions for the incident. Did it amplify other issues or create new vulnerabilities? |
| **Root Cause Analysis methodology used** | This field is optional, but recommended. A description of the methodology used to derive the issue described above (e.g., "5-Whys", Fishbone Diagram, Pareto Analysis, etc.) |

**Lessons Learned:** The Lessons Learned section describes what the organization learned from the incident, including what they did well and what they need to improve.

| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **What went well?** | A list of things that caused the incident to have less impact than it otherwise could have, such as early detection, rapid response, or good safety mechanisms. This section provides an opportunity for others to learn from the good practices of this CA Owner. |
| **What didn’t go well?** | A list of things that caused the incident to have more impact than it otherwise would have, such as missing checks or unclear documentation. Each item here MUST have at least one corresponding Action Item below and SHOULD provide opportunities for others to ensure they make similar improvements if they haven’t already. |
| **Where we got lucky?** | A list of things that went well, but which cannot be relied upon, such as early detection by an external security researcher or limited impact simply due to a small number of requests. Items here SHOULD generally also have corresponding Action Items, so that the CA Owner doesn’t have to rely on luck in the future. |
| **Other** | Any other type of "lesson learned" that does not otherwise fit in the above categories, e.g., internal/external circumstances or environmental conditions; discovery of problematic processes, policies, or workflows; communication gaps; resource challenges; task ownership; overlooked warning signs; underutilized tools; etc. Each item mentioned here MUST have at least one corresponding Action Item. |

**Action Items:** The Action Items section contains a list of remediation items that will be undertaken to ensure that similar incidents do not reoccur in the future. For example, if the Whiteboard field contains ‘revocation-delay’, the Action Items list MUST include steps reasonably calculated to prevent or reduce future revocation delays. Note that it is not sufficient for these action items to simply stop this incident, they MUST create additional protections to prevent future incidents.
  
| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **Action Item description** | A detailed description of the action to be taken. |
| **Kind** | A classification of whether the action will help *Prevent* future incidents, *Mitigate* the impact of future incidents, or *Detect* future incidents. CA Owners are encouraged to propose action items in all three categories, with an emphasis on Prevent and Mitigate. |
| **Corresponding Root Cause(s)** | The specific Root Cause that the Action intends to remediate (i.e., each problem/issue identified in the "Root Cause Analysis" and "What didn't go well" Sections MUST be mapped to at least one specific action item). |
| **Evaluation criteria** | Describe how the CA Owner will measure the effectiveness of the Action Item in addressing the Root Cause. Include how the public can also measure this impact, if applicable. CA Owners SHOULD prioritize objective and publicly measurable evidence (i.e., evidence that can be independently verified by the public, such as through Certificate Transparency log data, audit statements, CA policy documents, and public communications (e.g., website content, surveys, etc.)). While external metrics are preferred, these Guidelines recognize that some Action Items may have limited measurable outcomes. When objective metrics are not readily available, CA Owners SHOULD provide a qualitative assessment of the Action Item's effectiveness and explain how they will monitor its impact. Even after an Incident Report has been closed, CA Owners are strongly encouraged to provide periodic updates (e.g., 3, 6, and 12 months post-closure, or at other determined appropriate intervals) related to the ongoing efficacy of the Action Item, as measured against the evaluation criteria. This helps demonstrate a continued commitment to improvement and transparency.
| **Due date** | A date by which the action item will be complete. |
| **Status** | Describe the status of the action item using either "Ongoing", "Complete", "Delayed", or "Canceled". |

**Appendix:** The Appendix section is for all supporting data: log files, graphs and charts, etc. In the case of incidents that directly impact certificates (i.e., not only precertificates), the Appendix MUST disclose details related to the time-valid, including revoked, certificates affected by the incident.

For incidents affecting less than 10,000 certificates, a CA Owner MUST attach a comma separated listing of certificate details including the following fields for each:

| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **Precertificate SHA-256 hash** | The SHA-256 hash of the DER encoded precertificate. |
| **Certificate SHA-256 hash** | The SHA-256 hash of the DER encoded certificate. |
| **Subject** | The Subject field of the certificate. |
| **Issuer** | The Issuer field of the certificate. |
| **Not before** | The notBefore field of the certificate. |
| **Not after** | The notAfter field of the certificate. |
| **Serial #** | The Serial Number field of the certificate, in hex. |
| **dNSNames** | The dNSName appearing in the certificate. |
| **Is revoked?** | "Yes", "Planned","Delayed", or "N/A" (for expired) |
| **Revocation date** | Actual Date, Planned Date, or "N/A" |
| **Revocation reason** | The reasonCode corresponding with the certificate's entry on the CRL. |

For incidents affecting 10,000 or more certificates, a CA Owner MAY instead attach a text file where each line is of the form https://crt.sh/?sha256=[sha256 fingerprint of the certificate].

When the incident being reported involves an S/MIME certificate, if disclosure of personally identifiable information in the certificate MAY be contrary to applicable law, please provide at least the certificate serial number and SHA256 hash of the certificate.

##### Incident Closure Summary

The Incident Closure Summary allows a CA Owner to signal they believe an incident is ready for closure.

| Field                           | Description                              |  
|---------------------------------|------------------------------------------| 
| **Incident description** | A few sentences summarizing the incident. |
| **Incident Root Cause(s)** | A few sentences summarizing the root cause(s). |
| **Remediation description** | A few sentences summarizing the incident's remediation. |
| **Commitment summary** | A list of any ongoing commitments made in response to this incident beyond those described in the Action Items section. Ongoing commitments can be a useful representation of a CA Owner's continuous improvement efforts and should be considered distinct from, but complementary to Action Items included in the report given a broader scope and long-term or continuous timeframe that would otherwise result in the subject incident report being open for an extended period of time. |

### Illustrative practices

#### Are there examples of "good" practices?

1. **Be detailed and precise**:
   - Document, in detail, all findings and steps taken from discovery or initial notification through to remediation.
   - Include precise timestamps, technical data, and decision rationales.
   - Share relevant configurations, code snippets, or settings that were implicated, in compliance with security norms (i.e., do not disclose confidential or sensitive information).

2. **Respond promptly**:
   - Acknowledge receipt of the incident report quickly.
   - Provide initial assessments and expected timelines for resolution to keep stakeholders informed.
   - Respond to comments or questions within one business day.
  
3. **Be candid, transparent, and objective**:
   - Doing so allows community members to better understand report content, while also promoting integrity and transparency.

4. **Rely on comprehensive Root Cause Analysis frameworks**:
   - Use structured methodologies like the "Five Whys" or fault tree analysis to trace back to underlying issues.
   - Involve diverse teams (security, operations, engineering) to ensure a multi-faceted evaluation.

5. **Be proactive and thorough**:
   - Implement immediate fixes to mitigate any ongoing risks.
   - Develop long-term solutions that might involve architectural changes or the integration of new security tools and practices.

6. **Engage with the community**:
   - Participate in Web PKI forums and email distributions (e.g., public@ccadb.org) to both learn from and contribute to community knowledge.
   - Share incident learnings in a way that respects confidentiality but helps other organizations prevent similar issues.
   - Read and adopt best practices found in the [Bugzilla Incident Reports filed by other CA Owners](https://bugzilla.mozilla.org/buglist.cgi?product=CA%20Program&component=CA%20Certificate%20Compliance&bug_status=__open__&list_id=17075089).

7. **Share iterative updates**:
   - Provide an initial response, followed by regular updates aligned with ["When should Incident Reports be updated?"](#when-should-incident-reports-be-updated) as new information becomes available or as fixes are deployed..
   - Close the loop with a final summary once the issue is fully resolved, detailing the lessons learned and future prevention strategies.
  
8. **Respect external reporter privacy**:
   - If notified of an incident by an external, third party reporter, please respect their privacy by *only* disclosing their name if affirmatively approved to do so (e.g. say "we received a report from a community member" instead of explicitly naming individuals).
  
9. **Use Markdown formatting**:
   - Markdown formatting (e.g., headers, lists, bolding, italics, etc.) can promote clarity, readability, and accessability. Learn more about Markdown formatting [here](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

#### Are there examples of "bad" practices?

1. **Generic or evasive responses**:
   - Avoid generic statements that do not address specific issues raised in the report or in response to community questions or comments.
   - Refrain from providing non-committal or ambiguous answers that might be interpreted as evasive.

2. **Posturing**:
   - Avoid blaming others or external factors.
   - Resist downplaying the severity or implications of the incident.

3. **Claims that are subjective, unqualified opinions, speculative, or impossible to substantiate**:
   - Avoid making claims that are speculative or that cannot be corroborated (e.g. "there is no security impact due to this issue.")

4. **Non-acknowledgment of responsibility**:
   - Clearly accept responsibility where and when due, which helps in rebuilding trust and demonstrating accountability.

5. **Superficial Root Cause Analysis**:
   - Avoid superficial analyses that do not thoroughly explore all contributing factors.
   - Ensure that the analysis is not prematurely concluded, missing deeper systemic issues.

6. **Committing to opaque actions**:
   - Ensure actions and follow-up work items are detailed and specific.
   - Promote accountability by describing how the success of an action item can be evaluated as having been successful in addressing the root cause.

7. **Inadequate monitoring post-report**:
   - Establish mechanisms to monitor the long-term effectiveness of implemented changes.
   - Be ready to revisit and revise solutions if subsequent issues indicate that the initial response was not entirely effective.
  
#### Are there examples of "good" reports?

Here are some examples of good practice, where a CA Owner did most or all of the things recommended above:

- [Serving invalid or incomplete CRLs](https://bugzilla.mozilla.org/show_bug.cgi?id=1900129)
     - Clear Summary and Impact statements allow readers to quickly understand the scope of the incident
     - Detailed and thorough evaluation of existing safeguards that failed, allowing for an understanding of why the the incident was allowed to take place
     - Comments and questions from the community were responded to promptly.

- [keyCompromise key blocking deviation from CP/CPS](https://bugzilla.mozilla.org/show_bug.cgi?id=1886876)
     - Clear indication of Preliminary and Full Incident Reports.
     - Detailed timeline that identifies all policy, process, and software changes that contributed to the root cause, and an indication of when the incident began and ended.
     - Detailed Root Cause Analysis that offers background on the various conditions that gave rise to the issue.
     - Timely updates in response to questions posed, continued analysis, and changes to Action Items.
 
- [Failure to properly validate IP address](https://bugzilla.mozilla.org/show_bug.cgi?id=1876593)
     - Significant amount of background information that informs the timeline of the incident.
     - Clear identification of the contributing factors that contributed to the incident that notes how many of them avoided detection in the Root Cause Analysis.
     - Action Items that prevent, mitigate, and detect what didn’t go well.
     - Timely and detailed updates conveying Action Item status.

Upon adoption of the updated report templates described on this page, examples of good practice will be updated.
