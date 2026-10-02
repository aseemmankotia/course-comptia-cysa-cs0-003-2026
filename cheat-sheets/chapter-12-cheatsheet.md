## Chapter 12 Cheat Sheet: Exam Simulation & Time Management

### Exam Format
| Item | Value |
|---|---|
| Total questions | Up to 85 (MCQ + PBQ) |
| Time limit | 165 minutes |
| Passing score | 750 / 900 |
| Recommended pace | 60-90 sec/MCQ, 8-10 min/PBQ |

### Domain Weights (CS0-003)
| Domain | Weight | Review Priority |
|---|---|---|
| 1.0 Security Operations | ~33% | 1st |
| 2.0 Vulnerability Management | ~30% | 2nd |
| 3.0 Incident Response & Management | ~20% | 3rd |
| 4.0 Reporting & Communication | ~17% | 4th |

### Time Budget Strategy
1. Pass 1: Answer every MCQ you're confident about immediately.
2. Flag anything uncertain — do not stall.
3. Skip PBQs until MCQs are exhausted (PBQs cost 5-8x more time).
4. Pass 2: Attempt PBQs with remaining time.
5. Pass 3: Return to flagged MCQs, prioritizing Security Operations and Vulnerability Management domains first.
6. Check pace at 25%, 50%, 75% time markers — target roughly 21 questions answered per 25% block.

### CVSS v3.1 Severity Ranges
| Score | Severity |
|---|---|
| 0.0 | None |
| 0.1–3.9 | Low |
| 4.0–6.9 | Medium |
| 7.0–8.9 | High |
| 9.0–10.0 | Critical |

**Rule:** Base Score alone ≠ priority. Apply Environmental context (exposure, asset criticality, data sensitivity) before ranking remediation order.

### IR Phase Sequence (NIST SP 800-61)
Preparation → Detection & Analysis → Containment → Eradication → Recovery → Post-Incident Activity

| Phase | Action | Common Trap |
|---|---|---|
| Containment | Isolate, limit spread | Confused with Eradication |
| Eradication | Remove root cause | Confused with Recovery |
| Recovery | Restore to production | Attempted before Eradication complete |

### Cross-Domain Traps
- **False Positive** = alert on benign activity. **False Negative** = missed real threat. Tuning targets false positives; false negatives are worse for risk.
- **CVSS vs Context**: high Base Score on low-value isolated asset ranks below moderate score on exposed critical asset.
- **Containment vs Eradication**: isolating ≠ removing. If malware still exists on disk, you're still in Containment.

### Final Readiness Self-Check
- Score 85%+ on full-length, domain-weighted practice exams.
- Explain (don't just recall) containment vs eradication, CVSS prioritization logic, and false positive/negative triage.
- Confirm comfort with PBQ interfaces (drag-drop, log analysis, command-line simulation) under time pressure.
- Map every missed practice question back to its official CompTIA CS0-003 objective before exam day.
