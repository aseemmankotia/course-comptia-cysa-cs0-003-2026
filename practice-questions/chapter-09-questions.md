## Chapter 9: Incident Response: Preparation and Post-Incident Activity — Practice Questions

**Q1.** A financial services company suffers a ransomware incident. During recovery, the forensic analyst images the compromised server's hard drive but forgets to document who transferred the imaged drive to the legal team for 3 days. Which BEST describes the consequence?

A) The evidence remains admissible because the hash value still matches
B) The evidence can be re-validated by re-imaging the original drive
C) The gap only matters if the case goes to a civil, not criminal, court
D) The chain of custody is broken, making the evidence's integrity questionable in legal proceedings

<details>
<summary>Answer</summary>

**Correct: D**

Unbroken custody must be documented at every transfer point; an undocumented gap raises reasonable doubt regardless of technical integrity.

**Why the others are wrong:**
- A matching hash proves the file content wasn't altered, but it does not prove no unauthorized access or handling occurred during the undocumented gap.
- Re-imaging the original drive does not retroactively fix a custody gap for the evidence already collected and handled.
- Chain of custody requirements apply equally to civil and criminal proceedings; the type of court doesn't remove the requirement.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** During post-incident review of a data breach, the IR team wants to identify the single technical root cause quickly since the failure chain appears linear (unpatched vulnerability → exploit → lateral movement → exfiltration). Which RCA technique is MOST appropriate?

A) Fishbone (Ishikawa) diagram
B) 5 Whys
C) Fault tree analysis
D) SWOT analysis

<details>
<summary>Answer</summary>

**Correct: B**

5 Whys is ideal for a linear causal chain with a single traceable root cause, arrived at through iterative questioning.

**Why the others are wrong:**
- Fishbone diagrams are designed for multi-category, multi-factor causation (people/process/technology), overkill for a simple linear chain.
- Fault tree analysis models complex system failures with probability branches, which is beyond the scope of a straightforward linear incident.
- SWOT is a strategic planning framework, not a root cause analysis methodology.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An organization's IR plan lists the CISO as incident commander, but during a real incident, the CISO is unreachable for six hours and no one else has authority to declare containment actions. This failure indicates a gap in which IR plan element?

A) Root cause analysis process
B) Chain of custody procedures
C) Roles, responsibilities, and succession/backup authority
D) Business continuity plan RTO

<details>
<summary>Answer</summary>

**Correct: C**

IR plans must define primary AND backup decision authority so response isn't blocked by a single point of failure.

**Why the others are wrong:**
- RCA is a post-incident analysis activity, unrelated to real-time authority delegation.
- Chain of custody governs evidence handling, not command authority.
- RTO defines recovery timing targets, not who has decision-making power during response.

</details>

---

**Q4.** A SOC needs a document providing a decision-tree style, step-by-step response workflow specifically for handling phishing incidents (isolate mailbox, block sender, notify users, etc.). Which document should be created/used?

A) Phishing playbook
B) Business continuity plan
C) Incident response policy
D) Chain of custody form

<details>
<summary>Answer</summary>

**Correct: A**

Playbooks are tactical, incident-type-specific workflows, exactly matching the phishing-specific decision tree described.

**Why the others are wrong:**
- A BCP addresses continuity of business operations, not specific tactical response steps for an incident type.
- An IR policy is a high-level governance document setting authority and scope, not a step-by-step workflow.
- A chain of custody form tracks evidence handling, unrelated to incident response workflow steps.

</details>

---

**Q5.** Which exercise type allows the IR team to practice actual technical response actions on isolated test systems without impacting production, providing more realism than a discussion-based walkthrough but less risk than a full production failover?

A) Tabletop exercise
B) Functional exercise
C) Full-scale exercise
D) Checklist review

<details>
<summary>Answer</summary>

**Correct: B**

Functional exercises simulate real response actions in a controlled/test environment, forming the middle ground between discussion and full production drills.

**Why the others are wrong:**
- Tabletop exercises are purely discussion-based with no hands-on technical actions performed.
- Full-scale exercises involve live production systems and real failover, carrying much higher risk and realism.
- A checklist review simply verifies that plan components exist on paper; it does not exercise any response actions.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** When completing a chain-of-custody form for a seized USB drive, which field is MANDATORY to include for EVERY person who handled the evidence?

A) Date/time of transfer, purpose of transfer, and signature
B) Their annual performance review score
C) Their department's budget code
D) The evidence's insurance value

<details>
<summary>Answer</summary>

**Correct: A**

Standard custody documentation requires who, what, when, why, and a signature at every transfer point to maintain an unbroken evidentiary trail.

**Why the others are wrong:**
- Performance review data has no bearing on evidentiary integrity.
- Budget codes are administrative/financial data, irrelevant to custody tracking.
- Insurance valuation is unrelated to establishing possession and integrity of evidence.

</details>

---

**Q7.** During evidence collection at a live compromised server, per order of volatility, which data should be collected BEFORE the contents of RAM?

A) CPU cache and register contents
B) Hard disk image
C) Archived backup tapes
D) Network switch configuration logs

<details>
<summary>Answer</summary>

**Correct: A**

Order of volatility places CPU registers and cache as the most volatile data, meaning they must be collected before RAM contents are captured.

**Why the others are wrong:**
- Disk images are far less volatile than RAM and are collected later in the sequence.
- Archived backup tapes are the least volatile evidence type and collected last.
- Switch configuration logs are network/remote artifacts, collected after volatile memory per standard order.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What is the PRIMARY purpose of a post-incident lessons-learned meeting?

A) To assign disciplinary action to responsible employees
B) To identify process, tooling, and communication improvements for future incidents
C) To finalize the chain-of-custody documentation for legal proceedings
D) To calculate the exact financial cost of the incident for insurance claims

<details>
<summary>Answer</summary>

**Correct: B**

Lessons-learned is a blame-free process-improvement activity per the NIST post-incident activity phase, focused on refining future response.

**Why the others are wrong:**
- The meeting is explicitly meant to be blame-free; disciplinary action is not its purpose and can undermine honest reporting.
- Chain of custody documentation is a separate evidentiary process, unrelated to the lessons-learned discussion.
- Cost calculation may be referenced as an input but is not the primary purpose of the review.

</details>

---

