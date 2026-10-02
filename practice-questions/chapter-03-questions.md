## Chapter 3: Security Operations: Threat Intelligence, Threat Hunting, and MITRE ATT&CK — Practice Questions

**Q1.** A SOC analyst receives a report listing a file hash, three suspicious IP addresses, and a malicious domain associated with a recent phishing campaign. Six months later, the same threat actor group launches a new campaign using entirely different infrastructure but the identical spear-phishing-to-PowerShell-to-C2 execution chain. Which type of intelligence would have allowed analysts to detect the new campaign despite the changed infrastructure?

A) TTP-based detection derived from the actor's known behavior patterns
B) IOC feeds updated daily from commercial vendors
C) A larger list of blocked IP address ranges
D) Increased frequency of hash-based antivirus signature updates

<details>
<summary>Answer</summary>

**Correct: A**

TTPs describe HOW an actor operates (behavior), which persists across campaigns even when atomic indicators like hashes, IPs, and domains change. Detecting on the execution chain catches the actor regardless of infrastructure.

**Why the others are wrong:**
- IOC feeds only catch previously observed infrastructure — useless once the actor changes IPs/domains/hashes
- IP range blocking is still infrastructure-based and fails against new, unseen ranges
- Hash-based AV signatures fail immediately if the actor recompiles or repacks malware

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A threat hunter forms the statement: 'If an APT group is using living-off-the-land binaries for lateral movement, then we should see anomalous PsExec or WMI process chains originating from non-administrative endpoints.' She then queries EDR telemetry to test this statement. Which threat hunting methodology is being demonstrated?

A) Hypothesis-driven hunting
B) Signature-based detection
C) Indicator-based hunting
D) Automated alert triage

<details>
<summary>Answer</summary>

**Correct: A**

Hypothesis-driven hunting starts with a testable assumption (often informed by TTPs/MITRE ATT&CK) and proactively searches telemetry to confirm or refute it, rather than waiting for an alert.

**Why the others are wrong:**
- Signature-based detection is reactive and relies on pre-built rules, not a formed hypothesis
- Indicator-based hunting searches for known IOCs, not behavioral 'if-then' statements
- Automated alert triage responds to existing alerts rather than proactively forming and testing assumptions

</details>

---

**Q3.** An organization's critical infrastructure network is compromised by an actor using zero-day exploits, custom malware with anti-forensic capabilities, and multi-year dwell time focused on espionage rather than financial gain. Which threat actor type BEST matches this profile?

A) Cybercriminal syndicate
B) Hacktivist collective
C) Nation-state advanced persistent threat (APT)
D) Disgruntled insider

<details>
<summary>Answer</summary>

**Correct: C**

Zero-day usage, custom tooling, long dwell time, and espionage motive (not financial) are hallmark characteristics of nation-state APT groups with significant resources and strategic objectives.

**Why the others are wrong:**
- Cybercriminal syndicates are financially motivated and typically avoid burning expensive zero-days on long-term espionage
- Hacktivists seek public attention/disruption and rarely maintain years-long covert dwell time
- Insiders don't require zero-day exploits since they already have legitimate access

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A financial services company wants threat intelligence specific to attacks targeting other banks in its sector, including shared IOCs vetted by peer institutions. Which source BEST meets this requirement?

A) Open-source intelligence (OSINT) from public security blogs
B) A generic commercial threat feed covering all industries
C) Dark web forum monitoring performed in-house
D) An Information Sharing and Analysis Center (ISAC) for the financial sector

<details>
<summary>Answer</summary>

**Correct: D**

ISACs are sector-specific organizations where member institutions share vetted, relevant threat data (including IOCs and TTPs) specific to their industry — exactly matching the requirement for peer-vetted, sector-focused intel.

**Why the others are wrong:**
- OSINT is public and unvetted, lacking sector-specific context or peer validation
- Generic commercial feeds cover broad industries and dilute sector-specific relevance
- In-house dark web monitoring is resource-intensive and doesn't provide peer-vetted sharing

</details>

---

**Q5.** During an active MITRE ATT&CK-based investigation, an analyst wants to visualize which techniques a detected APT group historically uses and overlay that against the organization's current detection coverage to identify gaps. Which tool is designed for this specific purpose?

A) STIX/TAXII feed aggregator
B) A SIEM correlation rule builder
C) MITRE ATT&CK Navigator
D) An attack tree diagramming tool

<details>
<summary>Answer</summary>

**Correct: C**

ATT&CK Navigator is purpose-built to create layered visualizations of tactics/techniques, allowing analysts to map a group's known behavior against existing detection coverage and highlight gaps.

**Why the others are wrong:**
- STIX/TAXII is a format/protocol for sharing intel, not a visualization tool for ATT&CK coverage
- SIEM rule builders create detections but don't provide ATT&CK-aligned coverage visualization
- Attack trees model goal-oriented attack paths for threat modeling, not group-specific technique mapping

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** During a STRIDE threat modeling session, a developer identifies that an attacker could modify data in transit between two microservices without detection because messages are unsigned. Which STRIDE category does this threat fall under?

A) Tampering
B) Spoofing
C) Repudiation
D) Information Disclosure

<details>
<summary>Answer</summary>

**Correct: A**

Tampering refers to unauthorized modification of data — unsigned messages that can be altered in transit without detection is a textbook Tampering threat in the STRIDE model.

**Why the others are wrong:**
- Spoofing involves impersonating identity, not altering message content
- Repudiation is about denying having performed an action, not modifying data
- Information Disclosure involves exposing data to unauthorized parties, not altering it

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** An intelligence team gathers raw data from multiple feeds, correlates it, evaluates source reliability, and converts it into a finished report for the CISO before collecting feedback to refine future collection priorities. Which phase of the intelligence cycle occurs immediately BEFORE dissemination?

A) Collection
B) Analysis
C) Processing
D) Direction

<details>
<summary>Answer</summary>

**Correct: B**

The intelligence cycle order is: Direction → Collection → Processing → Analysis → Dissemination → Feedback. Analysis (evaluating reliability, correlating, drawing conclusions) directly precedes dissemination of the finished report.

**Why the others are wrong:**
- Collection is the raw data-gathering phase, which occurs before processing, not right before dissemination
- Processing converts raw data into a usable format but precedes analysis, not dissemination
- Direction is the initial phase where requirements are set, occurring at the start of the cycle

</details>

---

**Q8.** In the MITRE ATT&CK framework, T1566 represents Phishing. Which statement correctly describes the relationship between a Tactic and a Technique such as T1566?

A) A Tactic and a Technique are interchangeable terms for the same concept
B) A Technique describes the adversary's goal, while a Tactic describes how that goal is achieved
C) A Tactic represents the adversary's objective (the 'why'), while a Technique represents the specific method used to achieve it (the 'how')
D) Techniques only apply to nation-state actors, while Tactics apply to all threat actor types

<details>
<summary>Answer</summary>

**Correct: C**

In ATT&CK, Tactics are the adversary's tactical objectives (e.g., Initial Access), and Techniques (like T1566 Phishing) are the specific methods used to accomplish that objective. Sub-techniques further refine the technique.

**Why the others are wrong:**
- Tactics and Techniques are distinct hierarchy levels, not interchangeable
- This reverses the actual definitions — the technique is the 'how', not the 'why'
- The Tactic/Technique distinction applies to all actor types; it is not actor-type-specific

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

