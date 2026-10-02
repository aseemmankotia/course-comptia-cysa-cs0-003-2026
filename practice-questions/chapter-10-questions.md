## Chapter 10: Reporting and Communication: Vulnerability Management Reporting — Practice Questions

**Q1.** A healthcare organization must submit a vulnerability report to auditors as evidence of HIPAA Security Rule compliance. Which report type BEST satisfies this requirement?

A) An executive dashboard showing overall risk trend
B) A raw vulnerability scanner export with CVSS scores
C) A compliance/attestation report mapping findings to specific control requirements
D) A technical remediation runbook for IT operations

<details>
<summary>Answer</summary>

**Correct: C**

Auditors require evidence that findings and remediation activities map directly to specific regulatory controls; a compliance/attestation report is structured for this mapping.

**Why the others are wrong:**
- An executive dashboard is trend-focused for leadership, not control-mapped evidence.
- A raw scanner export lacks the control mapping and narrative auditors require.
- A remediation runbook is written for technical staff execution, not compliance evidence.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** The CISO is preparing a quarterly presentation for the board of directors. Which metric is MOST appropriate to include?

A) A list of every CVE identified during the quarter with CVSS base scores
B) Exact command-line syntax used to remediate a critical server vulnerability
C) A packet capture showing exploit traffic for a recent finding
D) Overall organizational risk reduction trend expressed as a percentage over time

<details>
<summary>Answer</summary>

**Correct: D**

Board-level audiences need high-level, business-impact-oriented trend data, not technical detail.

**Why the others are wrong:**
- A raw CVE list is too granular and technical for board consumption.
- CLI syntax is operational detail meant for IT staff, not executives.
- Packet captures are technical forensic artifacts irrelevant to board reporting.

</details>

---

**Q3.** Remediation of a critical finding is delayed because the affected system is a legacy mainframe still under an active vendor support contract, and no patch is available. Which remediation inhibitor category does this represent?

A) Business operations interruption
B) Budget constraint
C) Legacy system limitation
D) Staffing shortage

<details>
<summary>Answer</summary>

**Correct: C**

Lack of a vendor-supplied patch for an aging platform is the classic definition of a legacy system inhibitor.

**Why the others are wrong:**
- Business operations interruption applies when patching would halt a required process, not vendor patch unavailability.
- Budget constraint applies when funding is the blocker, not patch availability.
- Staffing shortage applies when there aren't enough personnel to perform the work, not a technical patch gap.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A vulnerability report contains exact patch versions, configuration change steps, and command-line remediation instructions. Which stakeholder group is this report written for?

A) Executive leadership
B) Board of directors
C) External compliance auditors
D) IT operations and system administrators

<details>
<summary>Answer</summary>

**Correct: D**

Technical, step-by-step remediation content is written for the operational staff who will actually perform the fix.

**Why the others are wrong:**
- Executives require summarized business-risk information, not technical steps.
- Board members need strategic risk trends, not operational instructions.
- Auditors need control-mapped compliance evidence, not remediation syntax.

</details>

---

**Q5.** Which stakeholder group should receive vulnerability findings framed around financial exposure and business impact rather than technical severity scores?

A) Security analysts
B) Help desk technicians
C) Network engineers
D) Executive management

<details>
<summary>Answer</summary>

**Correct: D**

Executives make resourcing and risk-acceptance decisions based on business and financial impact, not raw CVSS or technical detail.

**Why the others are wrong:**
- Security analysts need technical detail like CVSS and exploit data to act on findings.
- Help desk technicians handle tickets, not strategic risk framing.
- Network engineers need configuration-level technical detail, not financial impact summaries.

</details>

---

**Q6.** Which calculation correctly represents Mean Time to Remediate (MTTR)?

A) Total vulnerabilities found divided by scan frequency
B) Number of critical vulnerabilities divided by total vulnerabilities
C) Time elapsed between two consecutive vulnerability scans
D) Sum of (remediation date minus identification date) across findings, divided by number of vulnerabilities remediated

<details>
<summary>Answer</summary>

**Correct: D**

MTTR is the average elapsed time from when a vulnerability is identified to when it is remediated, calculated as the average of individual remediation durations.

**Why the others are wrong:**
- This describes a scan frequency ratio, not remediation time.
- This calculates the proportion of critical findings, a severity distribution metric, not MTTR.
- This describes scan interval/cadence, not the time to fix a vulnerability.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A vulnerability management report shows scan coverage of 65% for the quarter. What does this metric indicate?

A) 65% of identified vulnerabilities have been remediated
B) 65% of assets in the organization's inventory were scanned
C) 65% of completed scans passed compliance checks
D) Critical vulnerabilities were reduced by 65%

<details>
<summary>Answer</summary>

**Correct: B**

Scan coverage measures the percentage of known assets that were actually included in scanning activity, highlighting visibility gaps.

**Why the others are wrong:**
- This describes remediation rate, a separate metric from coverage.
- Compliance pass rate is unrelated to how much of the environment was scanned.
- Vulnerability reduction percentage is a trend metric, not coverage.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Across three consecutive quarterly scans, the same set of vulnerabilities keeps reappearing on the same hosts even though they were marked remediated. What does this high 'recurring findings' rate MOST likely indicate?

A) An improved and mature remediation process
B) An increase in scan frequency
C) A reduction in the organization's overall attack surface
D) A systemic root cause, such as a misconfigured baseline or broken patch process, that was never actually fixed

<details>
<summary>Answer</summary>

**Correct: D**

Recurring findings signal that remediation was not truly effective — often due to an unaddressed root cause like a golden-image misconfiguration or automated re-deployment reintroducing the flaw.

**Why the others are wrong:**
- A mature process would reduce, not repeat, the same findings.
- Scan frequency changes don't explain why the identical vulnerability reappears after remediation.
- A shrinking attack surface would reduce recurring findings, not increase them.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

