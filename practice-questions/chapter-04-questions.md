## Chapter 4: Security Operations: Automation, Orchestration, and SOAR for Efficiency — Practice Questions

**Q1.** A SOC analyst is overwhelmed by hundreds of low-severity phishing alerts daily, most of which are false positives after manual investigation. Which SOAR capability BEST addresses this problem?

A) Build an automated enrichment and triage playbook that checks sender reputation, attachment hash, and URL sandboxing before escalating only confirmed threats
B) Deploy a new SIEM correlation rule to suppress all phishing alerts
C) Increase the number of Tier 1 analysts assigned to the phishing queue
D) Disable email alerting until the phishing filter is retrained

<details>
<summary>Answer</summary>

**Correct: A**

Automated enrichment playbooks perform the repetitive investigation steps (reputation lookups, hash checks, sandbox detonation) and only surface alerts that meet escalation criteria, directly reducing alert fatigue.

**Why the others are wrong:**
- Suppressing all phishing alerts risks missing true positives — it eliminates visibility rather than improving triage quality.
- Adding headcount doesn't scale and doesn't address the root inefficiency of manual repetitive work.
- Disabling alerting entirely removes detection capability and is never an appropriate SOC response.

</details>

---

**Q2.** A SOAR platform receives an indicator from a threat intelligence feed and simultaneously updates a firewall block list, creates an EDR isolation task, and opens a ticket in the ITSM system — all from a single trigger. This is an example of:

A) Automation
B) Orchestration
C) Vulnerability scanning
D) Threat hunting

<details>
<summary>Answer</summary>

**Correct: B**

Orchestration is the coordination of actions across multiple, disparate security tools (firewall, EDR, ITSM) from one workflow trigger — connecting tools together.

**Why the others are wrong:**
- Automation refers to a single repetitive task executed without human intervention, not coordination across multiple platforms.
- Vulnerability scanning is unrelated — no scan is being performed here.
- Threat hunting is a proactive, hypothesis-driven human activity, not an automated multi-tool workflow.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A SOAR playbook automatically quarantines any host that generates three failed logins in five minutes, with no human review step. Overnight, this playbook quarantines 40 legitimate finance workstations during a scheduled password reset campaign, halting month-end processing. This incident BEST illustrates which risk?

A) Insufficient logging within the SOAR platform
B) Over-automation causing false-positive-driven business disruption
C) A misconfigured SIEM correlation rule
D) Inadequate vulnerability management scanning frequency

<details>
<summary>Answer</summary>

**Correct: B**

Fully automated response actions (like isolation) without a human-in-the-loop approval step can act on false positives, causing legitimate business impact — a core risk of over-automation the exam tests.

**Why the others are wrong:**
- Logging isn't the issue; the playbook logic and lack of approval gate is the problem.
- This isn't a correlation/detection accuracy issue — the alert logic fired as designed, but the automated response was too aggressive.
- Vulnerability management scanning frequency is unrelated to authentication alerting and automated isolation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which technology is specifically designed to integrate a SIEM, threat intel platform, firewall, and EDR into a single automated workflow engine with case management?

A) Intrusion Detection System (IDS)
B) Security Orchestration, Automation, and Response (SOAR) platform
C) Vulnerability scanner
D) Data Loss Prevention (DLP) system

<details>
<summary>Answer</summary>

**Correct: B**

SOAR platforms are purpose-built to connect (orchestrate) multiple security tools, automate repetitive tasks, and manage cases/playbooks from a single console.

**Why the others are wrong:**
- An IDS only detects and alerts on suspicious traffic; it does not orchestrate other tools.
- A vulnerability scanner identifies weaknesses but has no case management or cross-tool orchestration function.
- DLP prevents data exfiltration; it is one tool that could be orchestrated by a SOAR, not the orchestrator itself.

</details>

---

**Q5.** Which metric specifically measures the elapsed time between when a compromise first occurs and when the SOC identifies it?

A) Mean Time to Detect (MTTD)
B) Mean Time to Respond (MTTR)
C) Service Level Agreement (SLA)
D) Dwell time

<details>
<summary>Answer</summary>

**Correct: A**

MTTD measures time from initial compromise/occurrence to detection by the SOC — a primary metric SOAR automation is intended to reduce.

**Why the others are wrong:**
- MTTR measures time from detection to containment/remediation, not initial detection.
- SLA is a contractual performance target, not a measured incident-response metric.
- Dwell time is closely related (time attacker remains undetected) but is a broader concept typically measured from compromise to eradication, not strictly to detection — the exam distinguishes MTTD as the detection-specific metric.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A CSIRT is designing a new SOAR playbook that will disable user accounts flagged for potential compromise. Which configuration BEST balances speed with the risk of over-automation?

A) Fully automate account disablement with no analyst review to maximize response speed
B) Require the playbook to pause and request analyst approval before executing the account disablement action
C) Remove the playbook and handle all account compromise cases manually
D) Automatically disable the account and automatically re-enable it after 24 hours regardless of investigation status

<details>
<summary>Answer</summary>

**Correct: B**

A human-in-the-loop approval gate before high-impact/destructive actions preserves automation speed for enrichment while preventing false-positive-driven business disruption — the standard mitigation for over-automation risk.

**Why the others are wrong:**
- Fully automated disablement with no review is the exact over-automation risk the exam tests as a gotcha.
- Eliminating the playbook forfeits the MTTR/MTTD improvements automation provides.
- Auto re-enabling on a timer ignores investigation outcome and could restore access to a genuinely compromised account.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A junior analyst configures a script that automatically enriches every incoming IDS alert with WHOIS and geolocation data, but takes no further action and does not interact with any other security tool. This is best described as:

A) Orchestration
B) Threat modeling
C) Incident response plan
D) Automation

<details>
<summary>Answer</summary>

**Correct: D**

A single scripted task performed without human intervention and without coordinating multiple tools is automation — orchestration requires cross-tool coordination.

**Why the others are wrong:**
- Orchestration requires connecting and coordinating multiple disparate tools/systems, which is absent here.
- Threat modeling is a design-phase risk analysis activity unrelated to alert enrichment scripting.
- An incident response plan is a documented procedure, not a technical automation task.

</details>

---

**Q8.** What is the fundamental difference between automation and orchestration in a SOC context?

A) Automation requires human approval; orchestration never does
B) Automation executes a single repetitive task without human intervention; orchestration coordinates multiple tools/tasks into an end-to-end workflow
C) Automation applies only to network devices; orchestration applies only to endpoints
D) There is no meaningful difference — the terms are interchangeable on the exam

<details>
<summary>Answer</summary>

**Correct: B**

This is the exact distinction CySA+ tests: automation = one task, one system; orchestration = multiple tasks/tools coordinated together, often built on top of automated tasks.

**Why the others are wrong:**
- Human approval is a design choice (human-in-the-loop) that can apply to either automation or orchestration steps — it isn't the defining difference.
- Neither term is limited to a specific device category.
- The exam explicitly tests this as a distinct pair of terms — treating them as synonyms is a common wrong-answer trap.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

