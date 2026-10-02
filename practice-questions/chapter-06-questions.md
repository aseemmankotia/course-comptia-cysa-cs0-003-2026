## Chapter 6: Vulnerability Management: Analyzing and Prioritizing Vulnerability Data — Practice Questions

**Q1.** A vulnerability scanner reports CVE-2024-XXXX with a CVSS base score of 9.8 (Critical) on an isolated internal lab server with no network connectivity. The same scan reports a CVE with a base score of 7.5 (High) on an internet-facing web server that processes customer payment data. Which should be prioritized FIRST for remediation?

A) The 7.5 high vulnerability, because exposure (internet-facing) and asset criticality (payment data) increase real-world risk despite the lower base score
B) The 9.8 critical vulnerability, because CVSS base score always takes priority regardless of context
C) Both equally, since CVSS scores from the same scanner are directly comparable
D) Neither — wait for temporal metrics to be published before prioritizing

<details>
<summary>Answer</summary>

**Correct: A**

Context-aware prioritization weighs exposure and asset value alongside CVSS score; a lower-scored but internet-facing, high-value asset often represents greater real risk.

**Why the others are wrong:**
- Base score doesn't factor real-world reachability or exposure — treating it as absolute priority is the classic exam trap
- Scores from the same scanner aren't directly comparable without context of exposure and asset value
- Waiting delays remediation of a real, currently exploitable exposure; action shouldn't depend on temporal metric publication

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A security team detects unusual network traffic and threat intel confirms active exploitation in the wild of a vulnerability for which no vendor patch or CVE ID currently exists. What should the team do FIRST?

A) Wait for a CVE to be assigned before taking action
B) Ignore the threat until the vendor releases an official CVSS score
C) Apply compensating controls (IDS/IPS signatures, WAF rules, network segmentation) to reduce exposure while a permanent fix is developed
D) Immediately and permanently decommission all affected systems

<details>
<summary>Answer</summary>

**Correct: C**

Zero-day handling requires immediate risk reduction via compensating controls since no patch or official score exists yet.

**Why the others are wrong:**
- CVE assignment can take weeks; active exploitation demands immediate mitigation
- Absence of a CVSS score doesn't mean no risk — active exploitation is a strong exploitability indicator on its own
- Permanent decommissioning is disproportionate when less disruptive mitigations are available

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A vulnerability was scored CVSS base 6.5 (Medium) at disclosure. Two weeks later, functional exploit code is published publicly and active exploitation is observed across multiple organizations. How does this affect prioritization?

A) The base score changes automatically, raising it to Critical
B) No change in priority — only base score matters for remediation timelines
C) Priority should decrease since the vulnerability is now well documented
D) Priority should increase significantly because temporal factors (exploit code maturity, active exploitation) elevate real-world risk even though the base score doesn't change

<details>
<summary>Answer</summary>

**Correct: D**

Temporal metrics (Exploit Code Maturity, Report Confidence) reflect increased real-world exploitability and should drive reprioritization even when the base score is unchanged.

**Why the others are wrong:**
- Base score is static and based on inherent characteristics — it does not change with weaponization; only temporal/environmental scoring adjusts
- Ignoring temporal factors contradicts core exam guidance on context-aware prioritization
- More documentation with active exploitation increases risk, it does not decrease it

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** An analyst needs to prioritize 200 scan-detected vulnerabilities, but standard CVSS base scores don't account for the organization's specific network configuration and asset importance. Which scoring approach should be applied?

A) Continue using CVSS base scores only, since they are the industry standard
B) Recalculate CVE IDs for each vulnerability
C) Apply CVSS temporal scores only, ignoring base and environmental metrics
D) Calculate CVSS environmental scores, incorporating Confidentiality/Integrity/Availability Requirements and modified base metrics specific to the organization

<details>
<summary>Answer</summary>

**Correct: D**

The environmental metric group (CR/IR/AR plus modified base metrics) exists specifically to incorporate organization-specific context into scoring.

**Why the others are wrong:**
- Base-only scoring ignores organizational context, a gap the exam explicitly tests
- CVE IDs are identifiers, not scores, and are unrelated to prioritization scoring
- Temporal metrics alone omit organizational asset value and control context

</details>

---

**Q5.** A SQL injection vulnerability is flagged with a CVSS base score of 8.8 (High) on a database server. The organization has deployed a WAF with rules specifically blocking this attack pattern, and the database only accepts connections through the WAF. Which CVSS metric group should be adjusted to reflect this compensating control?

A) Environmental metrics — use modified base metrics (e.g., Modified Attack Complexity) to reflect the compensating control
B) Base metrics — modify Attack Vector to Physical
C) Temporal metrics — set Remediation Level to Unavailable
D) No adjustment possible — CVSS score is fixed once calculated

<details>
<summary>Answer</summary>

**Correct: A**

Environmental metrics allow modifying base metric values to reflect actual deployment conditions such as compensating controls, lowering effective severity.

**Why the others are wrong:**
- Base metrics represent inherent, unmodified characteristics and should not be altered to reflect deployed controls
- Remediation Level reflects patch availability, not a compensating control like a WAF
- CVSS environmental scoring exists explicitly to allow this kind of contextual adjustment

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** Given the CVSS v3.1 vector AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H, what is the resulting base score and severity rating?

A) 7.5, High
B) 6.5, Medium
C) 9.8, Critical
D) 10.0, Critical

<details>
<summary>Answer</summary>

**Correct: C**

This network-exploitable, low-complexity, no-privileges, no-interaction, unchanged-scope vector with high impact to all three CIA properties calculates to 9.8, within the Critical range.

**Why the others are wrong:**
- 7.5 corresponds to a less severe vector (e.g., reduced privileges or complexity), not this fully worst-case combination
- 6.5 undervalues the maximum impact scored on all three CIA components
- 10.0 is the theoretical maximum but this specific vector yields 9.8, not the absolute ceiling

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A vulnerability has a CVSS v3.1 base score of 7.5. Which severity rating does this fall under per the official CVSS qualitative severity rating scale?

A) Medium (4.0–6.9)
B) Critical (9.0–10.0)
C) Low (0.1–3.9)
D) High (7.0–8.9)

<details>
<summary>Answer</summary>

**Correct: D**

7.5 falls within the High range of 7.0–8.9 per the official CVSS v3.1 qualitative severity scale.

**Why the others are wrong:**
- Medium tops out at 6.9, below 7.5
- Critical starts at 9.0, above 7.5
- Low tops out at 3.9, far below 7.5

</details>

---

**Q8.** What is the key difference between a CVSS base score and a CVSS environmental score?

A) The base score is calculated by the vendor while the environmental score is calculated by the scanner vendor
B) There is no difference — they are two names for the same calculation
C) The environmental score always produces a higher numeric value than the base score
D) The base score reflects inherent, unchanging characteristics of a vulnerability, while the environmental score adjusts the base metrics to reflect an organization's specific security controls and asset criticality

<details>
<summary>Answer</summary>

**Correct: D**

This is the fundamental distinction tested repeatedly on the exam: base is static/inherent, environmental is organization-context-adjusted.

**Why the others are wrong:**
- Both can be calculated by anyone with the vector string; who calculates it is not the distinguishing factor
- They are distinct metric groups serving different purposes, not interchangeable names
- Environmental scores can be higher or lower than base scores depending on context — compensating controls lower it, higher asset value can raise it

</details>

---

