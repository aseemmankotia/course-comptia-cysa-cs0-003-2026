## Chapter 7: Vulnerability Management: Mitigating Controls and Vulnerability Response — Practice Questions

**Q1.** A retail company's threat intel feed flags a critical SQL injection vulnerability (CVSS 9.8) in a customer-facing payment application. The vendor patch requires a maintenance window that is 45 days out due to a mandatory UAT cycle. Which action should the analyst recommend FIRST while waiting for the patch?

A) Accept the risk until the maintenance window opens since the patch is already scheduled
B) Take the application offline until the patch is applied
C) Deploy a WAF rule to block known SQL injection patterns and enable enhanced logging on the affected endpoint
D) Transfer the risk by purchasing additional cyber insurance coverage

<details>
<summary>Answer</summary>

**Correct: C**

A WAF rule with signature-based blocking is a classic compensating control that reduces exploitability of a known injection vector without requiring code changes or downtime, buying time until full remediation.

**Why the others are wrong:**
- Risk acceptance is inappropriate for a CVSS 9.8 vulnerability on a payment system with a known compensating control available and PCI DSS implications.
- Taking the app offline satisfies availability concerns but destroys business continuity and is disproportionate when a compensating control exists.
- Insurance transfers financial loss, not the technical exposure, and does nothing to reduce likelihood of exploitation of an actively exploitable flaw.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** During a vulnerability scan, an analyst discovers a broken access control flaw allowing horizontal privilege escalation between customer accounts in a SaaS application the organization owns and maintains in-house. Which response represents true remediation rather than mitigation?

A) Rewriting the authorization logic to enforce server-side object-level access checks tied to session identity
B) Adding an IDS rule to alert on suspicious account ID enumeration patterns
C) Restricting the affected API endpoint to internal IP ranges only
D) Documenting the finding and scheduling a follow-up scan in 90 days

<details>
<summary>Answer</summary>

**Correct: A**

Remediation eliminates the root cause. Broken access control (OWASP A01) requires fixing the authorization logic itself, specifically enforcing object-level access control server-side so users cannot manipulate identifiers to access other accounts' data.

**Why the others are wrong:**
- An IDS alert only detects exploitation attempts after the fact; it does not fix or prevent the flaw — this is monitoring, not remediation.
- IP restriction is a compensating control that reduces exposure surface but does not fix the underlying broken authorization logic.
- Deferring with a rescan schedule is inaction, not remediation, and leaves the vulnerability exploitable.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A CISO reviews a vulnerability with a CVSS score of 4.2 discovered on an internal, air-gapped legacy system that is scheduled for decommission in 60 days. No patch exists from the vendor. What is the MOST appropriate disposition?

A) Immediate remediation by rebuilding the application on a supported platform
B) Risk transfer via a third-party managed security service
C) Risk acceptance, documented with compensating controls (network isolation) and an expiration tied to the decommission date
D) Escalate to emergency patch SLA regardless of the decommission timeline

<details>
<summary>Answer</summary>

**Correct: C**

Low severity, no available patch, existing compensating control (air-gap/isolation), and a defined short remaining lifespan make formal, time-boxed risk acceptance the proportionate and auditable decision.

**Why the others are wrong:**
- Rebuilding the application is disproportionate effort and cost for a system being decommissioned in 60 days.
- Risk transfer via a managed service doesn't apply to an air-gapped system with no external management access and doesn't address a missing patch.
- Treating a 4.2 (medium-low) finding on an isolated, soon-to-be-retired system as an emergency misallocates limited patching resources.

</details>

---

**Q4.** Which control BEST mitigates stored cross-site scripting (XSS) vulnerabilities in a web application's user comment feature?

A) Implementing output encoding/escaping combined with a Content Security Policy (CSP)
B) Enforcing TLS 1.2 or higher on all client connections
C) Rate limiting the comment submission endpoint
D) Enabling database-level encryption at rest for the comments table

<details>
<summary>Answer</summary>

**Correct: A**

Stored XSS occurs when untrusted input is rendered as executable script in the browser. Output encoding neutralizes script execution and CSP restricts which script sources the browser will execute, directly addressing the root cause.

**Why the others are wrong:**
- TLS protects data in transit but does nothing to prevent malicious script from being rendered by the browser.
- Rate limiting reduces automated abuse volume but does not prevent a single malicious payload from executing.
- Encryption at rest protects stored data confidentiality, not script execution in the rendered page.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Which secure coding practice provides the strongest defense against SQL injection at the code level (as opposed to a network-layer compensating control)?

A) Web application firewall signature rules
B) Parameterized queries / prepared statements
C) Network segmentation between the app tier and database tier
D) Increasing database connection timeout values

<details>
<summary>Answer</summary>

**Correct: B**

Parameterized queries separate SQL code from user-supplied data at the driver level, structurally preventing injection regardless of input content — the recommended secure SDLC fix, not just a mitigating control.

**Why the others are wrong:**
- A WAF is a compensating (network-layer) control that can be bypassed with obfuscated payloads; it doesn't fix the code.
- Segmentation limits blast radius but the injected query would still execute successfully against the database.
- Connection timeouts are unrelated to injection and have no security value here.

</details>

---

**Q6.** An organization's vulnerability management policy defines patch SLAs by risk rating: Critical, High, Medium, and Low. During an audit, the analyst finds a Critical-rated vulnerability (CVSS 9.6) that has been open for 25 days with no patch applied and no documented exception. Per common industry SLA tiering, which statement is TRUE?

A) This is within acceptable range since Critical items typically allow up to 30 days
B) This is an SLA breach; Critical vulnerabilities are typically remediated within 15 days and require a documented exception if the deadline cannot be met
C) SLA breaches only apply to internet-facing assets, so internal exposure is not a concern
D) SLAs do not apply until the vulnerability has been confirmed via manual penetration testing

<details>
<summary>Answer</summary>

**Correct: B**

Common risk-based SLA frameworks used in CySA+ scenarios set Critical remediation targets around 15 days (High ~30, Medium ~90, Low ~180). Exceeding this without a formally approved exception constitutes an SLA breach requiring escalation.

**Why the others are wrong:**
- 30 days is the typical target for High, not Critical severity, so this understates the breach.
- SLA policies apply organization-wide; internal assets can still be leveraged for lateral movement and are within scope of vulnerability management programs.
- Scanner/CVSS-confirmed findings start the SLA clock; waiting for manual pentest confirmation is not standard practice and would inappropriately delay remediation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** What is 'virtual patching' in the context of vulnerability response?

A) Applying the vendor's official patch in a staging environment before production
B) A patch that is applied automatically without human review
C) Removing the vulnerable software entirely and replacing it with an alternative product
D) Using a network or application-layer control (such as an IPS/WAF signature) to block exploitation of a known vulnerability without modifying the vulnerable code

<details>
<summary>Answer</summary>

**Correct: D**

Virtual patching is a compensating control technique that blocks exploit traffic at the network/application layer (IPS, WAF) when the actual code-level patch cannot be deployed immediately, reducing risk while remediation is scheduled.

**Why the others are wrong:**
- Staging deployment is normal patch testing, not 'virtual' patching — it still modifies the underlying code eventually.
- Automatic patching without review describes unattended patch management, unrelated to the virtual patching concept.
- Replacing the software is remediation via substitution, not a compensating/virtual control.

</details>

---

**Q8.** Which pairing correctly matches the vulnerability response term with its definition?

A) Mitigation = permanently eliminating the root cause of the vulnerability
B) Risk transfer = reducing the likelihood of exploitation through compensating controls
C) Remediation = purchasing insurance to cover potential financial loss from exploitation
D) Risk acceptance = a documented, authorized decision to take no further action because the risk is within tolerance

<details>
<summary>Answer</summary>

**Correct: D**

Risk acceptance is the formal, documented decision by authorized risk owners to tolerate a known risk without further action, typically because remediation cost/impact exceeds the risk itself.

**Why the others are wrong:**
- Mitigation reduces risk/impact via compensating controls; it does NOT eliminate root cause — that's remediation.
- Risk transfer shifts financial or operational impact to a third party (e.g., insurance, outsourcing); reducing likelihood via controls is mitigation, not transfer.
- Remediation means fixing/removing the vulnerability itself (patching, code fix); buying insurance is risk transfer, not remediation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

