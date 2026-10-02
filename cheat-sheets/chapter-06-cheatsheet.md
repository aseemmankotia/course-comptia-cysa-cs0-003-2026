## CVSS v3.1 Quick Reference

### Severity Rating Scale
| Score Range | Rating |
|---|---|
| 0.0 | None |
| 0.1–3.9 | Low |
| 4.0–6.9 | Medium |
| 7.0–8.9 | High |
| 9.0–10.0 | Critical |

### Metric Groups
| Group | Components | Changes Over Time? |
|---|---|---|
| Base | AV, AC, PR, UI, S, C, I, A | No — static/inherent |
| Temporal | E (Exploit Code Maturity), RL (Remediation Level), RC (Report Confidence) | Yes |
| Environmental | Modified Base metrics + CR/IR/AR | Yes — org-specific |

### Base Metric Values
| Metric | Values (least→most severe) |
|---|---|
| AV (Attack Vector) | Physical < Local < Adjacent < Network |
| AC (Attack Complexity) | High < Low |
| PR (Privileges Required) | High < Low < None |
| UI (User Interaction) | Required < None |
| S (Scope) | Unchanged < Changed |
| C/I/A | None < Low < High |

### Classic Vector Example
`AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H` → **9.8, Critical** (network, no auth, no interaction, full CIA impact).

### Prioritization Beyond the Number
| Factor | Effect on Priority |
|---|---|
| Internet-facing exposure | Increases |
| High asset value/criticality | Increases |
| Active exploitation observed | Increases sharply |
| Public/weaponized exploit code | Increases |
| Compensating control already deployed (WAF, segmentation) | Decreases (reflect via Environmental metrics) |
| Isolated/internal-only, low-value asset | Decreases |

**Rule of thumb:** CVSS Base score = theoretical worst case. Real prioritization = Base score + exposure + asset value + exploitability/weaponization signals + existing compensating controls.

### Zero-Day Handling Checklist
1. No CVE/patch exists yet — do NOT wait for one.
2. Apply compensating controls immediately: IDS/IPS signatures, WAF rules, network segmentation, feature disablement.
3. Monitor threat intel for active exploitation indicators.
4. Apply vendor patch once released; retire compensating controls only after validated remediation.

### CVE Format
`CVE-YYYY-NNNN` (year + ≥4-digit sequence). CVE = identifier only; CVSS = severity score. They are independent — a CVE can exist with no CVSS score yet, and CVSS scoring can be recalculated (temporal/environmental) without a new CVE.
