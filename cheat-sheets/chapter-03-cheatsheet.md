## Chapter 3 Cheat Sheet: Threat Intel, Hunting & MITRE ATT&CK

### Intelligence Cycle (6 phases, cyclical)
| Phase | Activity |
|---|---|
| Direction | Define intel requirements/priorities |
| Collection | Gather raw data (feeds, OSINT, sensors) |
| Processing | Normalize/decrypt/translate raw data |
| Analysis | Correlate, evaluate reliability, draw conclusions |
| Dissemination | Deliver finished intel to stakeholders |
| Feedback | Refine future Direction based on results |

### IOC vs TTP
| | IOC | TTP |
|---|---|---|
| Definition | Atomic artifact (hash, IP, domain) | Behavioral pattern of actor's operations |
| Attacker cost to change | Low (easy) | High (hard) |
| Detection durability | Short-lived | Long-lasting |

### Pyramid of Pain (bottom→top, increasing attacker pain)
Hash Values → IP Addresses → Domain Names → Network/Host Artifacts → Tools → **TTPs** (hardest to change)

### Threat Intel Sources
| Source | Characteristics |
|---|---|
| OSINT | Free, public, unvetted (blogs, Twitter/X, forums) |
| ISAC | Sector-specific, peer-vetted (FS-ISAC, H-ISAC, etc.) |
| Commercial Feed | Paid, vendor-curated, broad or specialized |

### Threat Actor Types & Motivations
| Actor | Motivation | Sophistication |
|---|---|---|
| Nation-state/APT | Espionage, strategic advantage | High, zero-days, long dwell time |
| Cybercriminal | Financial gain | Medium-high, ransomware/fraud |
| Hacktivist | Ideology/political disruption | Low-medium, seeks publicity |
| Insider | Revenge, financial, ideology | Varies; has legitimate access already |

### MITRE ATT&CK Structure
- **14 Tactics** (the 'why' — e.g., Initial Access, Persistence, Exfiltration) — IDs: TA####
- **Techniques** (the 'how' — e.g., T1566 Phishing) — IDs: T####
- **Sub-techniques** (specific variant — e.g., T1566.001 Spearphishing Attachment) — IDs: T####.###
- **Navigator**: visualizes technique coverage/gaps as heatmap layers

### STRIDE (Threat Modeling)
| Letter | Threat | Violates |
|---|---|---|
| S | Spoofing | Authentication |
| T | Tampering | Integrity |
| R | Repudiation | Non-repudiation |
| I | Information Disclosure | Confidentiality |
| D | Denial of Service | Availability |
| E | Elevation of Privilege | Authorization |

### Attack Trees
Root = attacker's goal; branches/leaves = methods (AND/OR logic) to reach the goal.

### Hypothesis-Driven Threat Hunting (proactive, not alert-driven)
1. Form hypothesis (from ATT&CK/intel) → 2. ID needed telemetry → 3. Investigate → 4. Confirm/refute → 5. Improve detections

### Exam Gotchas
- IOC ≠ TTP: exam scenarios testing 'infrastructure changed but detection still worked' = TTP-based.
- Sector-specific sharing requirement = ISAC, not generic commercial feed.
- 'TA' prefix = Tactic; 'T' alone = Technique; decimal suffix = Sub-technique.
- Espionage + zero-day + long dwell = nation-state, not cybercriminal.
