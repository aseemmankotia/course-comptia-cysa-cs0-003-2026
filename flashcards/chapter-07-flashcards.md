## Chapter 7: Vulnerability Management: Mitigating Controls and Vulnerability Response — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | SQL Injection — best code-level fix? | Parameterized queries/prepared statements. Exam tip: WAF rules are a compensating control, NOT the code-level remediation. |
| 2 | Stored XSS — two-part fix? | Output encoding/escaping + Content Security Policy (CSP). Encoding neutralizes payload, CSP restricts script sources as defense-in-depth. |
| 3 | Broken Access Control (OWASP A01) — root cause fix? | Enforce server-side, object-level authorization checks tied to session identity. IP restriction or logging = mitigation, not remediation. |
| 4 | Virtual Patching — definition | Using IPS/WAF signatures to block exploitation of a known vuln without touching the vulnerable code. Classic compensating control when patch isn't deployable yet. |
| 5 | Remediation vs Mitigation | Remediation = eliminates root cause (patch, code fix, replace). Mitigation = reduces likelihood/impact without fixing root cause (WAF, segmentation, IDS alerting). |
| 6 | Risk Acceptance vs Risk Transfer | Acceptance = documented decision to tolerate risk as-is (no action). Transfer = shift impact to third party (insurance, outsourcing/managed service), risk itself still exists. |
| 7 | Typical patch SLA — Critical severity | ~15 days remediation target in common risk-based SLA frameworks. Breach requires documented, approved exception. |
| 8 | Typical patch SLA — High severity | ~30 days remediation target (common industry tiering used in CySA+ scenarios). |
| 9 | Typical patch SLA — Medium/Low severity | Medium ~90 days, Low ~180 days. Lower severity = longer allowable remediation window. |
| 10 | Vulnerability response workflow order | Detection → Validation/Prioritization (CVSS/risk score) → Assign & Track → Remediate/Mitigate/Accept/Transfer → Verify (rescan) → Report/Close. |
| 11 | When is a compensating control acceptable instead of immediate patching? | When patch isn't yet available/tested, causes unacceptable downtime, or exception is formally approved — must be documented with a remediation timeline, not indefinite. |
| 12 | Secure SDLC — where does vulnerability scanning belong? | Integrated at multiple phases: SAST during coding, DAST during testing, dependency/SCA scanning at build, and pen testing pre-release — 'shift left' reduces cost of late-stage fixes. |
