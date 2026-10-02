## Chapter 9 Cheat Sheet: IR Preparation & Post-Incident Activity

### NIST IR Lifecycle (Order Matters)
| Phase | Focus |
|---|---|
| 1. Preparation | Plans, playbooks, roles, training, tooling |
| 2. Detection & Analysis | Identify and scope the incident |
| 3. Containment/Eradication/Recovery | Stop spread, remove cause, restore |
| 4. Post-Incident Activity | RCA, lessons learned, plan updates |

### IR Plan vs Playbook vs Runbook
| Document | Level | Example |
|---|---|---|
| IR Plan | Strategic — roles, authority, comms plan | Who declares an incident |
| Playbook | Tactical — incident-type workflow | Ransomware playbook decision tree |
| Runbook | Operational — single task steps | "Isolate host via EDR" steps |

### RCA Methods
| Method | Best For |
|---|---|
| 5 Whys | Simple, linear causal chain, single root cause |
| Fishbone (Ishikawa) | Multiple contributing factors (People/Process/Tech/Environment) |
| Fault Tree Analysis | Complex system failures, probability-based branching |

### Exercise Types (Realism vs Risk)
| Type | Description | Risk/Realism |
|---|---|---|
| Tabletop | Discussion-based walkthrough | Low risk, low realism |
| Functional | Simulated actions on test systems | Medium |
| Full-scale | Live actions on production systems | High risk, high realism |

### Chain of Custody Essentials
- Record for EVERY transfer: **who, what, when, where, why, signature**
- Hash evidence before AND after imaging (e.g., `sha256sum file.img`) — hashes must match
- Use a **write blocker** before imaging/analyzing original media
- Any undocumented gap = broken chain = questionable admissibility

### Order of Volatility (Most → Least Volatile)
1. CPU registers/cache
2. RAM
3. Swap/paging file
4. Disk
5. Remote logs
6. Archival/backup media

### Lessons-Learned Process
- Hold **within days to ~2 weeks** of closure while details are fresh
- **Blame-free / no-fault** format — goal is process improvement, not discipline
- Outputs must feed back into: updated playbooks/runbooks + policy/process changes
- Document what worked, what didn't, and assign owners to remediation items

### BC/DR Alignment
- **BCP/DRP** define **RTO** (how fast to recover) and **RPO** (how much data loss is acceptable)
- IR plan **references** RTO/RPO during recovery — it does not define them
- IR and BC/DR teams must coordinate on communication plans and escalation paths

### Common Exam Traps
- Assuming a matching hash alone preserves admissibility despite a custody gap — it does not
- Confusing tabletop (tests the plan) with full-scale (tests team execution)
- Choosing Fishbone for a simple linear failure chain — use 5 Whys instead
- Treating lessons-learned as a disciplinary meeting rather than process improvement
