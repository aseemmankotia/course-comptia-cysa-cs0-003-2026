## Chapter 11 Cheat Sheet: Incident Response Reporting and Escalation

### Incident Declaration Criteria
| Trigger | Example |
|---|---|
| Confirmed unauthorized access | Attacker logged in with stolen creds |
| Data confidentiality breach | PII/PHI exfiltrated |
| Malware execution w/ impact | Ransomware encrypting systems |
| Policy violation w/ significant risk | Insider disabling security controls |

**Exam note:** Declaration is based on *confirmed impact meeting threshold*, not every raw alert.

### Escalation Order (typical)
1. SOC analyst → IR Team Lead
2. IR Lead → Management/Executives (per Severity SLA)
3. Legal Counsel (evidence, liability, regulatory obligations)
4. PR/Communications (external messaging)
5. Regulators (if legally required)
6. Customers (last, after legal review)

### Severity-Based Communication Timing
| Severity | Typical Notification Window |
|---|---|
| Sev 1 (Critical) | Immediate/within 30–60 min to execs |
| Sev 2 (High) | Within hours |
| Sev 3/4 (Low/Med) | Standard reporting cycle |

**Exam note:** Missing SLA windows = documented process failure, not automatic severity change.

### Stakeholder Roles During Active Incident
| Stakeholder | Role |
|---|---|
| Legal | Regulatory compliance, liability, evidence/legal hold |
| PR/Comms | Public messaging, brand protection |
| Executives | Resource authorization, business decisions |
| Customers | Notified last, post-legal review |

### RCA Report to Leadership — Must Include
- Root cause (technical, but summarized)
- Timeline of events
- Business impact
- Remediation actions taken
- Cost estimate
- Written in **non-technical** language

### Lessons-Learned Meeting
- **Blameless** post-mortem
- Goal: identify process gaps, create **tracked** action items
- Not for: drafting press releases, assigning blame, or cost calculation alone

### Post-Incident Metrics
| Metric | Definition |
|---|---|
| Dwell Time | Initial compromise → detection |
| MTTD | Mean Time to Detect |
| MTTC | Detection → containment |
| MTTR | Detection → full recovery |
| Cost | Recovery + downtime + reputational damage |

**Common exam trap:** Confusing dwell time (compromise→detection) with MTTC (detection→containment). Read the metric definition carefully — the exam tests exact boundaries between metrics.
