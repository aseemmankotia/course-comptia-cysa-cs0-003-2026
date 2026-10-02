## Chapter 11: Reporting and Communication: Incident Response Reporting and Escalation — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | What triggers formal 'incident declaration' vs. just logging an alert? | Confirmed impact meeting predefined criteria (e.g., confirmed unauthorized access, data exfiltration, malware execution with business impact). Exam tip: declaration triggers the IR plan's communication and escalation procedures. |
| 2 | Dwell time — definition | Time from initial compromise to detection. Exam tip: distinguish from Time to Containment (detection→isolation) and MTTR (detection→full recovery). |
| 3 | Time to Containment (MTTC) | Measures time from detection to isolating/stopping the threat's spread. Reported post-incident to evaluate SOC response speed. |
| 4 | Who must review public statements before release during a breach? | Legal counsel (compliance/liability) AND PR/communications (messaging). Exam tip: both required, neither alone is sufficient. |
| 5 | Purpose of a lessons-learned (post-mortem) meeting | Blameless review to identify process gaps and create tracked action items — NOT to assign blame. Exam tip: 'blameless' is a key term the exam favors. |
| 6 | Severity-based communication timing | Higher severity incidents (Sev 1/critical) require faster executive/stakeholder notification per the IR plan's SLA (e.g., within 30–60 min). Exam tip: missing this SLA delays business decisions and legal actions. |
| 7 | What should an RCA report to leadership include? | Root cause, timeline, business impact, remediation actions taken, and cost — written in non-technical, business-focused language. |
| 8 | Typical post-incident metrics reported to leadership | Dwell time, Time to Detect (MTTD), Time to Contain (MTTC), Time to Recover (MTTR), and total incident cost (recovery + downtime + reputational). |
| 9 | Who should be notified about legal hold / evidence preservation during an incident? | Legal counsel — they issue and manage legal hold notices to preserve evidence for potential litigation or regulatory investigation. |
| 10 | Escalation path stakeholders during an active incident (common exam list) | IR team lead → Management/Executives → Legal → PR/Communications → Regulators (if required) → Customers (last, after legal review). |
| 11 | Why declare incidents formally instead of treating all alerts equally? | Prevents resource exhaustion and unnecessary stakeholder disruption; reserves full escalation/communication procedures for events meeting defined impact thresholds. |
| 12 | Common exam trap: customer notification timing | Customer notification typically occurs AFTER legal review and regulatory assessment, not immediately upon discovery. Premature notification can create legal liability and misinformation. |
