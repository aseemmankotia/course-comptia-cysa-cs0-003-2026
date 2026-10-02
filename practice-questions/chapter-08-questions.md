## Chapter 8: Incident Response: Attack Frameworks and Core IR Activities — Practice Questions

**Q1.** During malware analysis, a responder observes an implant that has already exploited a browser vulnerability and is now periodically calling out to an external IP address every 60 seconds to receive commands. Which Cyber Kill Chain phase does this beaconing activity represent?

A) Installation
B) Command and Control
C) Exploitation
D) Actions on Objectives

<details>
<summary>Answer</summary>

**Correct: B**

Regular callbacks to an external host for instructions define the Command and Control (C2) phase, which occurs after the implant is installed and before the attacker executes final objectives.

**Why the others are wrong:**
- Installation is the act of planting the backdoor/persistence mechanism, which already happened before the beaconing started.
- Exploitation is the moment the vulnerability is triggered to gain code execution, not the ongoing communication afterward.
- Actions on Objectives is the final phase where the attacker achieves their goal (e.g., exfiltration, destruction), not the communication channel itself.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company's ransomware outbreak has been isolated to a single VLAN. The IR team now removes malicious registry run keys, deletes dropped binaries, and rebuilds two servers from verified clean images before returning them to production. In what order do these two NIST-aligned IR phases occur?

A) Eradication, then Recovery
B) Recovery, then Eradication
C) Containment, then Detection
D) Post-Incident Activity, then Containment

<details>
<summary>Answer</summary>

**Correct: A**

Eradication removes the root cause (malicious keys, binaries) from affected systems; Recovery follows by restoring systems to normal, verified operation.

**Why the others are wrong:**
- Recovery cannot precede Eradication — restoring a still-infected system reintroduces the threat.
- Detection already occurred prior to containment being applied in this scenario; it does not follow containment.
- Post-Incident Activity (lessons learned) happens after Recovery is complete, not before Containment.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An analyst needs to stop an actively spreading worm from reaching additional hosts while preserving RAM contents on the infected machine for forensic analysis. Which action best achieves short-term containment?

A) Power off the infected host immediately
B) Isolate the host via VLAN/ACL segmentation without shutting it down
C) Reimage the host from a golden image
D) Apply a vendor patch to all hosts in the environment

<details>
<summary>Answer</summary>

**Correct: B**

Network segmentation (VLAN quarantine or ACL blocks) stops lateral spread immediately while keeping the host powered on, preserving volatile memory for later capture — the definition of short-term containment.

**Why the others are wrong:**
- Powering off destroys volatile memory (RAM), losing evidence such as running processes and network connections.
- Reimaging is an eradication/recovery activity, not containment, and destroys forensic evidence.
- Patching is a long-term eradication measure and does not stop the immediate spread of an already-active worm.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A threat intelligence team is documenting the C2 domains, hop-point IP addresses, and hosting providers used in an ongoing campaign. Which Diamond Model of Intrusion Analysis core feature does this data populate?

A) Adversary
B) Capability
C) Victim
D) Infrastructure

<details>
<summary>Answer</summary>

**Correct: D**

Infrastructure covers the physical or logical assets an adversary uses to deliver capabilities and maintain access, including C2 domains, IP addresses, and hosting services.

**Why the others are wrong:**
- Adversary refers to the threat actor or group responsible for the intrusion, not the network assets they use.
- Capability refers to the tools, malware, or techniques the adversary employs, not the delivery infrastructure.
- Victim refers to the targeted organization, system, or person, not the attacker's supporting infrastructure.

</details>

---

**Q5.** A SOC wants to map observed adversary behavior in a recent intrusion to a standardized library of tactics and techniques (e.g., T1566 Phishing, T1059 Command and Scripting Interpreter) to guide detection engineering and threat hunting. Which framework should they use?

A) MITRE ATT&CK
B) Cyber Kill Chain
C) Diamond Model of Intrusion Analysis
D) OWASP Top 10

<details>
<summary>Answer</summary>

**Correct: A**

MITRE ATT&CK is a knowledge base of adversary tactics and techniques (14 Enterprise tactics as of the current matrix) with technique IDs used to map behavior for detection and hunting.

**Why the others are wrong:**
- Cyber Kill Chain describes a linear seven-phase attack progression, not a granular technique library with IDs.
- The Diamond Model analyzes individual intrusion events via four core features; it does not catalog specific techniques.
- OWASP Top 10 is a web application vulnerability list, not an adversary behavior/technique framework.

</details>

---

**Q6.** During analysis of an incident involving unauthorized data extraction via a crafted SQL statement submitted through a login form, which resource should the analyst reference for standardized vulnerability classification and remediation guidance?

A) NIST SP 800-61
B) OWASP Top 10
C) Cyber Kill Chain
D) Diamond Model of Intrusion Analysis

<details>
<summary>Answer</summary>

**Correct: B**

OWASP Top 10 (current edition released 2021, still the reference standard as of 2026) categorizes web application vulnerability classes such as Injection, and provides remediation guidance directly applicable to a SQL injection incident.

**Why the others are wrong:**
- NIST SP 800-61 defines the incident response lifecycle process, not application vulnerability classifications.
- The Cyber Kill Chain describes the stages of an attack campaign, not application-layer weakness categories.
- The Diamond Model analyzes intrusion event relationships, not specific web vulnerability classes.

</details>

---

**Q7.** Per NIST SP 800-61, an analyst has just confirmed that unusual outbound traffic is a genuine security incident rather than a false positive. Which activity should be performed next, still within the Detection and Analysis phase, before any containment action is taken?

A) Reimage the affected host from a clean backup
B) Determine the scope and impact of the incident
C) Remove the malware binary from disk
D) Restore the host to the production network

<details>
<summary>Answer</summary>

**Correct: B**

The Detection and Analysis phase requires scoping and prioritizing the incident (affected systems, data, business impact) before moving into Containment, Eradication, and Recovery.

**Why the others are wrong:**
- Reimaging is a Recovery activity performed after containment and eradication, not during analysis.
- Removing the malware binary is an Eradication activity, which occurs after containment is established.
- Restoring to production is the final Recovery step, well after scope has been determined and containment applied.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which sequence correctly represents the seven phases of the Cyber Kill Chain in order?

A) Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command and Control, Actions on Objectives
B) Reconnaissance, Delivery, Weaponization, Installation, Exploitation, Command and Control, Actions on Objectives
C) Weaponization, Reconnaissance, Exploitation, Delivery, Command and Control, Installation, Actions on Objectives
D) Reconnaissance, Weaponization, Exploitation, Delivery, Installation, Actions on Objectives, Command and Control

<details>
<summary>Answer</summary>

**Correct: A**

Lockheed Martin's Cyber Kill Chain defines the sequence as Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command and Control, and Actions on Objectives.

**Why the others are wrong:**
- This swaps Weaponization and Delivery order and misplaces Exploitation relative to Installation.
- This places Exploitation before Delivery and Command and Control before Installation, both incorrect.
- This swaps Actions on Objectives and Command and Control, placing the final phase before C2 is established.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

