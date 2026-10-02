## Chapter 11: Reporting and Communication: Incident Response Reporting and Escalation — Practice Questions

**Q1.** A SOC analyst confirms that an attacker has exfiltrated 50GB of customer PII from a database server. The organization's incident response plan requires formal incident declaration once data confidentiality is confirmed to be breached. What should the analyst do FIRST?

A) Formally declare the incident and notify the incident response team lead per the escalation matrix
B) Immediately notify all customers whose data was affected
C) Wait until root cause is determined before declaring an incident
D) Shut down the affected server without notifying anyone

<details>
<summary>Answer</summary>

**Correct: A**

Formal incident declaration triggers the documented escalation process, ensuring the right stakeholders (IR lead, legal, management) are engaged in the correct order before external notifications occur.

**Why the others are wrong:**
- Customer notification comes later, often after legal review and regulatory requirements are assessed — premature notification can create legal liability.
- Root cause analysis happens during/after containment, not as a prerequisite to declaring the incident — declaration should happen as soon as impact criteria are met.
- Unilateral action without following the escalation path violates IR plan communication procedures and can destroy evidence or coordination.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** During an active ransomware incident affecting a hospital's patient record system, which stakeholder combination MUST be engaged before any public statement is released?

A) IT helpdesk and marketing intern
B) Only the CISO, since PR can draft statements independently
C) Legal counsel and public relations/communications team
D) External vendors who sold the affected software

<details>
<summary>Answer</summary>

**Correct: C**

Legal counsel must review statements for regulatory compliance (e.g., breach notification laws, HIPAA) and liability exposure, while PR crafts the actual messaging — both are required before any public release.

**Why the others are wrong:**
- Helpdesk staff have no authority or expertise to shape public-facing incident communications.
- PR alone lacks legal expertise on regulatory disclosure obligations and liability language, risking non-compliant statements.
- Vendors are not internal stakeholders responsible for organizational public communications and may have conflicting interests.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A company's incident response plan defines a Severity 1 (critical) incident as requiring executive notification within 30 minutes of declaration. Two hours after a critical breach is confirmed, the executive team still has not been informed. What is the MOST likely consequence of this failure being tested on the exam?

A) No consequence, as long as the incident is eventually resolved
B) The incident automatically downgrades to Severity 2
C) Violation of the communication SLA defined in the IR plan, potentially delaying critical business and legal decisions
D) The SOC analyst is legally liable for the breach

<details>
<summary>Answer</summary>

**Correct: C**

Severity-based communication timing (SLAs) exists so decision-makers can authorize resources, engage legal/PR, and make business continuity decisions quickly. Missing this window delays critical response actions.

**Why the others are wrong:**
- Timing violations have real consequences — delayed decisions, regulatory exposure, and reputational damage.
- Severity is based on impact/scope, not on whether communication SLAs were met.
- Individual analysts are not typically held personally liable; organizational accountability applies through IR governance.

</details>

---

**Q4.** Which document is BEST suited for communicating root cause analysis findings to executive leadership after an incident is closed?

A) Raw SIEM log export with all correlated alerts
B) An executive summary report highlighting root cause, business impact, remediation actions, and cost, without technical jargon
C) The full packet capture (PCAP) files from the incident
D) A verbal briefing with no written follow-up

<details>
<summary>Answer</summary>

**Correct: B**

Executives need concise, business-impact-focused summaries — root cause, impact, remediation, and cost — not raw technical data. A written report also provides an audit trail.

**Why the others are wrong:**
- Raw log exports are too technical and voluminous for executive consumption.
- PCAP files require deep technical analysis and are not actionable for leadership decision-making.
- Verbal-only briefings lack a documented record for compliance, audit, and follow-up tracking.

</details>

---

**Q5.** A lessons-learned meeting is scheduled after a major incident. Which activity is the PRIMARY purpose of this meeting?

A) Identifying process gaps and creating tracked action items to prevent recurrence
B) Assigning blame to the analyst who missed the initial alert
C) Drafting the public press release
D) Calculating the exact financial cost of the breach for insurance purposes

<details>
<summary>Answer</summary>

**Correct: A**

Lessons-learned (post-incident review) meetings focus on identifying what worked, what failed, and creating actionable, tracked improvements — a blameless, process-improvement focus.

**Why the others are wrong:**
- Blameless post-mortems are the industry best practice; assigning individual blame discourages future reporting and is not the meeting's purpose.
- Press release drafting is a PR/legal function handled during active response, not the lessons-learned meeting.
- Cost calculation is part of post-incident metrics reporting but is not the primary purpose of the lessons-learned session itself.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** An organization measures the time between initial compromise and detection as part of its post-incident metrics reporting. What is this metric called?

A) Mean Time to Contain (MTTC)
B) Mean Time to Recover (MTTR)
C) Dwell time
D) Service Level Agreement (SLA) breach rate

<details>
<summary>Answer</summary>

**Correct: C**

Dwell time is the duration an attacker remains undetected inside the environment, measured from initial compromise to detection — a key post-incident metric reported to leadership.

**Why the others are wrong:**
- MTTC measures time from detection to containment, not initial compromise to detection.
- MTTR measures time to full recovery/restoration of services, a later stage metric.
- SLA breach rate is unrelated to detection timing; it tracks failures to meet service-level commitments.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which post-incident metric would BEST help leadership evaluate the effectiveness of the SOC's containment procedures?

A) Number of phishing emails received company-wide that month
B) Total number of employees in the IT department
C) Number of open job requisitions in the security team
D) Time to containment (from detection to isolation of the threat)

<details>
<summary>Answer</summary>

**Correct: D**

Time to containment directly measures how quickly the SOC isolated the threat after detection, a key indicator of response process effectiveness.

**Why the others are wrong:**
- Phishing volume reflects threat landscape exposure, not SOC containment performance.
- Staffing count is irrelevant to procedural effectiveness measurement.
- Open job requisitions relate to hiring, not incident response performance.

</details>

---

**Q8.** What is the primary reason an incident response plan defines formal criteria for 'declaring' an incident rather than treating every alert as an incident?

A) To reduce the number of alerts the SIEM generates
B) To avoid ever having to notify executives
C) To automatically close low-priority tickets
D) To ensure resources, communication plans, and escalation procedures are only triggered for events that meet a defined threshold of confirmed impact

<details>
<summary>Answer</summary>

**Correct: D**

Formal declaration criteria (e.g., confirmed unauthorized access, data loss, system compromise) prevent resource exhaustion and unnecessary stakeholder disruption by reserving full IR/escalation processes for events meeting a defined severity/impact threshold.

**Why the others are wrong:**
- Declaration criteria don't affect SIEM alert volume, which is a detection/tuning concern, not a communication process concern.
- The goal is appropriate, not zero, executive notification — critical incidents still require it.
- Declaration criteria are unrelated to ticket lifecycle management for low-priority items.

</details>

---

