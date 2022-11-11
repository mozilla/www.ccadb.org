# Incidents # 
Incidents happen. Things do not always go as planned, and that can be okay. However, when incidents occur, the underlying issue (i.e., root cause) should be identified and remediated to discourage the incident from occurring again. Formally documenting the incident in a report encourages an understanding of all contributing root cause(s), and it presents the opportunity to clearly communicate a remediation plan to reduce the probability of its reoccurrence. 

Depending on the root programs in which a CA Owner participates, it may be required to:
* create [Audit Incident Reports](incident-report#audit-incident-reports) when audits have non-conformities, qualifications, or modified opinions.
* create [Incident Reports](incident-report#incident-reports) for all other incidents.

These reports provide lessons learned and transparency about the steps the CA takes to address the immediate issue and prevent future issues. If the underlying problem goes unfixed, then other issues that share the same root cause will subsequently surface. Additionally, incident reports help the Web PKI ecosystem as a whole because they promote continuous improvement, information sharing, and highlight opportunities to define and adopt improved practices, policies, and controls.

## Incident Reports ##

The purpose of incident reporting is to help us work together to build a more secure web. Therefore, the incident report should share lessons learned that could be helpful to all CA Owners in building better systems. The incident report should explain how systems or processes failed, how the mis-issuance or incident was made possible, and why the problem was not detected earlier. In addition to the timeline of responding to and resolving the incident, the incident report should explain how the CA Owner's systems or processes will be made more robust, and how other CAs may learn from the incident.

Incident reports are created as a bug in [Bugzilla](https://bugzilla.mozilla.org/buglist.cgi?product=NSS&component=CA%20Certificate%20Compliance&resolution=---&list_id=16285934) under the CA Program:CA Certificate Compliance component.

Each incident should result in an incident report written as soon as the problem is fully diagnosed and (temporary or permanent) measures have been put in place to ensure it will not reoccur. If the permanent fix will take significant time to implement, you should not wait until this is done before issuing the report. Incident reports should be published as soon as possible, and certainly within two weeks of the initial issue being reported. 

There should be a single incident report for each distinct matter, and CA Owners should submit an additional, separate incident report when:

* Policy requires the revocation of one or more certificates by a certain deadline, such as those in BR section 4.9, but that deadline will not be or has not been met by the CA Owner.
* In the process of researching one incident, another incident with a distinct root cause and/or remediation is discovered.
* After an incident is marked resolved in Bugzilla, the incident reoccurs.
* The incident report may well repeat things previously said in discussions or Bugzilla comments. This is entirely expected. The report should be a summary of previous findings. The existence of data in discussions or Bugzilla comments does not excuse a CA Owner from the task of compiling a proper incident report.

The incident report should include at least the following topics:

1. How your CA first became aware of the problem (e.g., via a problem report submitted to your Problem Reporting Mechanism, a discussion in the MDSP or CCADB public mailing list, a Bugzilla bug, or internal self-audit), and the time and date.
2. A timeline of the actions your CA took in response. A timeline is a date-and-time-stamped sequence of all relevant events. This may include events before the incident was reported, such as when a requirement became applicable, a document changed, a bug was introduced, or an audit was performed.
3. Whether your CA has stopped, or has not yet stopped, certificate issuance or the process giving rise to the problem or incident. A statement that you have stopped will be considered a pledge to the community; a statement that you have not stopped requires an explanation.
4. In a case involving certificates, a summary of the problematic certificates. For each problem: the number of certificates, and the date the first and last certificates with that problem were issued. In other incidents that do not involve enumerating the affected certificates (e.g., OCSP failures, delayed responses, etc.), please provide other similar statistics, aggregates, and a summary for each type of problem identified. This will help measure the severity of each problem.
5. In a case involving TLS server certificates, the complete certificate data for the problematic certificates. The recommended way to provide this is to ensure each certificate is logged to CT and then list the fingerprints or crt.sh IDs, either in the report or as an attached spreadsheet, with one list per distinct problem. It is also recommended that you use this form in your list "https://crt.sh/?sha256=[sha256-hash]", unless circumstances dictate otherwise. When the incident being reported involves an SMIME certificate, if disclosure of personally identifiable information in the certificate may be contrary to applicable law, please provide at least the certificate serial number and SHA256 hash of the certificate. In other cases not involving a review of affected certificates, please provide other similar, relevant specifics, if any.
6. Explanation about how and why the mistakes were made or bugs introduced, and how they avoided detection until now.
7. List of steps your CA is taking to resolve the situation and ensure that such a situation or incident will not be repeated in the future. The steps should include the action(s) for resolving the issue, the status of each action, and the date each action will be completed.

Incident reports should be updated when:
* Identifying changes to a step for resolution,
* Completion of a resolution step, or
* Delays in completing a resolution step.

It should be expected that the incident reports provide sufficient detail about the root cause, and the remediation, that would allow other CAs or members of the public to implement an equivalent solution.

For example, it's not sufficient to say that "human error" of "lack of training" was a root cause for the incident, nor that "training has been improved" as a solution. While a lack of training may have contributed to the issue, it's also possible that error-prone tools or practices were required, and making those tools less reliant on training is the correct solution. When training or a process is improved, the CA Owner is expected to provide specific details about the original and corrected material, and specifically detail the changes that were made, and how they tie to the issue. Training alone should not be seen as a sufficient mitigation, and focus should be made on removing error-prone manual steps from the system entirely.

Here are some examples of good practice, where a CA did most or all of the things recommended above:
* [Failure to provide OCSP Responses for some certificates](https://bugzilla.mozilla.org/show_bug.cgi?id=1753123)
* [Incorrect OCSP responses](https://bugzilla.mozilla.org/show_bug.cgi?id=1763203)

## Audit Incident Reports ##

When audits are performed, an Audit Attestation Letter (AAL) may document qualifications or non-conformities (i.e., findings) that were identified during the audit. Audit incident reports are created as a bug in Bugzilla under the CA Program:CA Certificate Compliance component and should include at least the following topics:
1. Issue # (where each non-conformity, qualification, and/or modified opinion is represented as a separate issue):
2. Issue Description:
3. Root Cause of Issue:
4. Remediation Plan for this Issue:

The remediation plan includes the action(s) for resolving the issue, the status of each action, and the date each action will be completed. The audit incident report summary in Bugzilla should include the CA Owner name and "Findings in 20XX Audit", where XX is the year the audit period or point-in-time ended (e.g., CA ABC: Findings in 2022 Audit). 

Audit incident reports should be updated when:
* Identifying changes to the presented issue remediation plan(s),
* Completion of issue remediation action(s), or
* Delays in completing issue remediation action(s).
