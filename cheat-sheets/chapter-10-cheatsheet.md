## Chapter 10 Cheat Sheet: Vulnerability Management Reporting

### Report Types by Purpose
| Report Type | Audience | Content Focus |
|---|---|---|
| Compliance/Attestation | Auditors, Compliance | Findings mapped to specific controls (PCI DSS, HIPAA, etc.) |
| Executive Summary | C-suite, Board | Risk trend %, financial/business impact, resourcing asks |
| Technical Remediation Plan | IT Ops, Sysadmins | Patch versions, CLI steps, configs, owners, deadlines |
| Risk-Prioritization Report | Risk committee, Management | CVSS + asset criticality + business exposure combined |

### Key Metrics/KPIs
| Metric | Definition | Watch For |
|---|---|---|
| MTTR | Avg(remediation date − identification date) | Speed of fixing, not detection |
| Scan Coverage | % of inventoried assets actually scanned | Visibility gap even with good remediation numbers |
| Recurring Findings | Same vuln reappears post-remediation | Signals systemic/root-cause failure, not isolated miss |
| Remediation Rate | % of open findings closed in period | Pair with severity — closing only Lows inflates rate |

### Remediation Inhibitors (know all 4)
| Category | Example |
|---|---|
| Business Operations | Patching would halt a 24/7 production system |
| Legacy Systems | No vendor patch exists for outdated platform |
| Budget | No funds for replacement hardware/software |
| Staffing | Not enough qualified personnel to execute fixes |

### Stakeholder Communication Map
| Stakeholder | Needs | Avoid Giving Them |
|---|---|---|
| Executives/Board | Risk trend, $ impact, strategic decisions | Raw CVEs, CLI commands |
| IT Operations | Exact remediation steps, owners, deadlines | High-level business trend only |
| Compliance/Auditors | Control-mapped evidence, attestation | Unstructured technical scan dumps |

### Risk Prioritization Framing
Don't rank by CVSS alone. Combine:
1. Technical severity (CVSS)
2. Asset criticality (is it a crown-jewel system?)
3. Business exposure (data sensitivity, external-facing?)

### Remediation Plan Must Include
Finding → Affected Asset → Risk Rating → Owner → Remediation Steps → Target Date → Verification Method

### Exam Traps
- Choosing 'highest CVSS' as the top priority when asset criticality/exposure isn't considered.
- Sending technical CLI-level detail to executives (wrong audience match).
- Confusing scan coverage (breadth of scanning) with remediation rate (speed of fixing).
- Misclassifying inhibitors — read scenario carefully for budget vs. legacy vs. staffing vs. operations language.
