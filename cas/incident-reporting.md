# Incidents
Incidents can happen. Things do not always go as planned, and that can be okay. However, when incidents occur, the underlying issues (i.e., root causes) must be identified and remediated to discourage the incident from occurring again. Formally documenting the incident in a report encourages an understanding of all contributing root causes, and it presents the opportunity to clearly communicate a remediation plan to reduce the probability of reoccurrence. 

## Objectives and Expectations

The purpose of Incident Reporting is to help us work together to build a more secure web. 

Depending on the root programs in which a CA Owner participates, it may be required to:
* create [Audit Incident Reports](audit-incident-report) when audits have non-conformities, qualifications, or modified opinions.
* create [Incident Reports](incident-report) for all other incidents.

These reports provide lessons learned and transparency about the steps the CA Owner takes to address the immediate issue and prevent future issues. If the underlying problem goes unfixed, then other issues that share the same root cause will subsequently surface. Additionally, Incident Reports help the Web PKI ecosystem as a whole because they promote continuous improvement, information sharing, and highlight opportunities to define and adopt improved practices, policies, and controls.

CA Incident Reports are expected to:
- be candid, timely, and transparent;
- clearly and objectively communicate the scope, impact, and severity of an incident;
- help community members understand the relevant architectures, implementations, operations, and external dependencies surrounding an incident;
- demonstrate a detailed understanding of the root cause(s) of an incident;
- unambiguously explain how systems, processes, and/or policies failed; 
- describe the circumstances that prevented the problem(s) from being detected earlier;
- describe a clear timeline of a CA Owner's actions while responding to and remediating an incident;
- include a detailed and measurable explanation of actions taken or planned by the CA Owner that demonstrate a substantive commitment of how the CA Owner's systems, policies, and/or processes will be made more robust (i.e., demonstrate continuous improvement); and
- share lessons learned that could be helpful to all CA Owners in building better systems policies, and/or processes.

### Incident Reporting: Good Practices

1. **Be Detailed and Precise**:
   - Document, in detail, all findings and steps taken from discovery or initial notification through to remediation.
   - Include precise timestamps, technical data, and decision rationales.
   - Share relevant configurations, code snippets, or settings that were implicated, in compliance with security norms (i.e., do not disclose confidential or sensitive information).

2. **Respond Promptly**:
   - Acknowledge receipt of the incident report quickly.
   - Provide initial assessments and expected timelines for resolution to keep stakeholders informed.
   - Respond to comments or questions within 24 hours.
  
3. **Be Candid, Transparent, and Objective**:
   - Doing so allows community members to better understand report content, while also promoting integrity and transparency.

4. **Rely on Comprehensive Root Cause Analysis Frameworks**:
   - Use structured methodologies like the "Five Whys" or fault tree analysis to trace back to underlying issues.
   - Involve diverse teams (security, operations, engineering) to ensure a multi-faceted evaluation.

5. **Be Proactive and Thorough**:
   - Implement immediate fixes to mitigate any ongoing risks.
   - Develop long-term solutions that might involve architectural changes or the integration of new security tools and practices.

6. **Engage with the Community**:
   - Participate in Web PKI forums and email distributions (e.g., public@ccadb.org) to both learn from and contribute to community knowledge.
   - Share incident learnings in a way that respects confidentiality but helps other organizations prevent similar issues.
   - Read and adopt best practices found in the Bugzilla Incident Reports filed by other CA Owners (i.e., the "[CA Certificate Compliance](https://bugzilla.mozilla.org/buglist.cgi?product=CA%20Program&component=CA%20Certificate%20Compliance&bug_status=__open__&list_id=17075089)" component in Bugzilla).  

7. **Share Iterative Updates**:
   - Provide an initial response, followed by regular updates as new information becomes available or as fixes are deployed.
   - Close the loop with a final summary once the issue is fully resolved, detailing the lessons learned and future prevention strategies.
  
8. **Respect External Reporter Privacy**:
   - If notified of an incident by an external, third party reporter, please respect their privacy by *only* disclosing their name if affirmativley approved to do so (i.e., use "We received a report from a community member" instead of explicitly naming individuals).

###  Incident Reporting: Bad Practices

1. **Generic or Evasive Responses**:
   - Avoid generic statements that do not address specific issues raised in the report or in response to community questions or comments.
   - Refrain from providing non-committal or ambiguous answers that might be interpreted as evasive.

2. **Posturing**:
   - Avoid blaming others or external factors.
   - Resist downplaying the severity or implications of the incident.

3. **Claims that are Subjective, Unqualified Opinions, Speculative, or Impossible to Substantiate**:
   - Avoid making claims that are speculative or that cannot be corroborated (i.e., "there is no security impact due to this issue."

4. **Non-acknowledgment of Responsibility**:
   - Clearly accept responsibility where and when due, which helps in rebuilding trust and demonstrating accountability.

5. **Superficial Root Cause Analysis**:
   - Avoid superficial analyses that do not thoroughly explore all contributing factors.
   - Ensure that the analysis is not prematurely concluded, missing deeper systemic issues.

6. **Committing to Opaque Actions**:
   - Ensure actions and follow-up work items are detailed and specific.
   - Promote accountability by describing how the success of an action item can be evaluated as having been successful in addressing the root cause.

7. **Inadequate Monitoring Post-Incident**:
   - Establish mechanisms to monitor the long-term effectiveness of implemented changes.
   - Be ready to revisit and revise solutions if subsequent issues indicate that the initial response was not entirely effective.
  
## Useful References:

- Root Cause and Incident Analysis Methodologies:
     - [Chesterton’s Fence](https://fs.blog/chestertons-fence/)
     - [5 Whys](https://en.wikipedia.org/wiki/Five_whys)
     - Multi/Second Order Thinking ([1](https://fs.blog/second-order-thinking/), [2](https://betterletter.substack.com/p/second-order-thinking), and [3](https://medium.com/@noahmp/second-order-thinking-3fc2a224b131
))
     - [CATWOE Analysis](https://www.toolshero.com/problem-solving/catwoe-analysis/)
     - [Cause and Effect / Fishbone or Ishikawa](https://en.wikipedia.org/wiki/Ishikawa_diagram)
     - [Drilling Down](https://sigma.software/about/media/problem-solving-techniques-part-two#2.-drill-down)
- SRE Handbook
     - [Chapter 14 - "Managing Incidents"](https://sre.google/sre-book/managing-incidents/)
     - [Chapter 15 - "Postmortem Culture"](https://sre.google/sre-book/postmortem-culture/)
