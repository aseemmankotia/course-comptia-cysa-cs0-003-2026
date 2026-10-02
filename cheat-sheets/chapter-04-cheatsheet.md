## Chapter 4 Cheat Sheet: SOAR, Automation & Orchestration (Domain 1.4)

### Core Definitions
| Term | Definition | Exam Trap |
|---|---|---|
| Automation | Single repetitive task executed without human input, on one system | Confused with orchestration |
| Orchestration | Coordinating multiple disparate tools/tasks into one end-to-end workflow | Requires 2+ tools connected |
| SOAR | Platform combining orchestration + automation + case/response management | 3 functions in the name |

### Key Metrics (know direction of improvement)
| Metric | Definition | SOAR Impact |
|---|---|---|
| MTTD | Time from compromise to detection | ↓ via automated correlation/enrichment |
| MTTR | Time from detection to containment/remediation | ↓ via automated response playbooks |
| Dwell Time | Time attacker undetected, compromise → eradication | ↓ overall via faster MTTD + MTTR |

### Playbook Types (exam scenarios)
- **Enrichment playbook**: adds context (WHOIS, geolocation, reputation, sandbox detonation) — no destructive action, reduces alert fatigue.
- **Response playbook**: takes action — block IP, isolate host, disable account, open ticket.
- **Orchestrated multi-tool playbook**: one trigger fires actions across SIEM + firewall + EDR + ITSM simultaneously.

### Human-in-the-Loop Rule
Destructive/high-impact actions (account disable, host isolation, firewall block on production traffic) should include an **approval gate**. Fully automated destructive actions = **over-automation risk**.

### Over-Automation Risk (heavily tested gotcha)
False positive → automated destructive action → business disruption (e.g., blocking legit users, isolating finance workstations). Mitigation: approval gates, tuning detection logic, phased rollout of automation.

### Automation vs Orchestration — Quick Test
- "One task, one tool, no coordination" → **Automation**
- "Multiple tools acting together from one trigger" → **Orchestration**
- "Platform that does both + manages cases" → **SOAR**

### Common Wrong Answers to Avoid
- Calling a single enrichment script "orchestration" (it's automation unless multiple tools are coordinated).
- Confusing MTTD with dwell time (dwell time is broader, spans to eradication).
- Choosing "remove automation entirely" as fix for over-automation (correct fix = add approval gate/human-in-the-loop, not eliminate automation).
- Assuming SLA is a measured incident metric (it's a contractual target, not MTTD/MTTR).
