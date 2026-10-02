# Chapter 7 Cheat Sheet: Vulnerability Management — Controls & Response

## Vulnerability Class → Primary Control Mapping
| Vulnerability Class | Root-Cause Fix (Remediation) | Compensating Control (Mitigation) |
|---|---|---|
| SQL Injection | Parameterized queries / prepared statements | WAF signature rules |
| Stored/Reflected XSS | Output encoding + input validation | CSP header |
| Broken Access Control | Server-side object-level authZ checks | Restrict endpoint by network/role |
| Insecure Design | Threat modeling, redesign at architecture level | Additional monitoring/logging |
| Missing Patch (unpatched CVE) | Vendor patch applied | Virtual patch via IPS/WAF, network isolation |

## Response Options — Definitions
| Term | Meaning | Root cause fixed? |
|---|---|---|
| Remediation | Eliminate vulnerability (patch, code fix, replace) | Yes |
| Mitigation | Reduce likelihood/impact via compensating control | No |
| Risk Acceptance | Documented decision to tolerate risk as-is | No |
| Risk Transfer | Shift impact to third party (insurance, outsourcing) | No |

## Typical Patch SLA Tiers (risk-based, org policy example)
| Severity (CVSS) | Target Remediation Window |
|---|---|
| Critical (9.0–10.0) | ~15 days |
| High (7.0–8.9) | ~30 days |
| Medium (4.0–6.9) | ~90 days |
| Low (0.1–3.9) | ~180 days |

Exception handling: missed SLA requires documented, approved exception with compensating control + new target date. Undocumented breach = audit finding.

## Vulnerability Response Workflow
1. Detection (scan/threat intel/pentest)
2. Validation & Prioritization (CVSS + asset criticality + exploitability)
3. Assignment & Tracking (ticket, owner, SLA clock starts)
4. Disposition: Remediate / Mitigate / Accept / Transfer
5. Verification (rescan confirms closure)
6. Reporting & Closure (audit trail, metrics)

## Secure SDLC Integration Points
- **Design:** threat modeling — addresses Insecure Design class
- **Code:** SAST, secure coding standards (input validation, parameterized queries)
- **Build/Dependencies:** SCA (software composition analysis) for vulnerable libraries
- **Test:** DAST, penetration testing
- **Deploy:** virtual patching / WAF tuning as stopgap
- **Shift Left principle:** earlier detection = cheaper fix

## Exam Traps
- Choosing 'accept risk' for a Critical/high-exposure finding when a compensating control is feasible — usually wrong.
- Confusing WAF/IPS rules (mitigation) with actual code remediation.
- Assuming insurance = mitigation (it's transfer — risk itself is unchanged).
- Forgetting that risk acceptance MUST be documented/approved, not silent inaction.
