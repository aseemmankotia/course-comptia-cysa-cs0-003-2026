# CS0-003 Ch.8: Attack Frameworks & Core IR Activities

## Cyber Kill Chain (Lockheed Martin) — 7 Phases, In Order
| # | Phase | Description |
|---|-------|-------------|
|1|Reconnaissance|Research target (OSINT, scanning)|
|2|Weaponization|Pair exploit with payload|
|3|Delivery|Transmit weapon (email, USB, web)|
|4|Exploitation|Trigger vulnerability, gain execution|
|5|Installation|Install backdoor/persistence|
|6|Command and Control (C2)|Establish remote channel|
|7|Actions on Objectives|Achieve goal (exfil, destroy, encrypt)|

**Exam trap:** Confusing Exploitation (code runs) with Installation (persistence planted). Also watch order of C2 vs Actions on Objectives.

## Diamond Model of Intrusion Analysis
| Core Feature | Represents |
|---|---|
|Adversary|Threat actor/group|
|Capability|Malware, tools, exploits, TTPs|
|Infrastructure|C2 domains, IPs, hosting, hop points|
|Victim|Targeted org/system/person|

Meta-features connecting an event: Timestamp, Phase (maps to Kill Chain), Result, Direction, Methodology, Resources.

## Framework Selection
| Need | Use |
|---|---|
|High-level attack sequence|Cyber Kill Chain|
|Relate adversary/infra/capability/victim|Diamond Model|
|Granular technique IDs, detection/hunting|MITRE ATT&CK (14 Enterprise tactics)|
|Web app vulnerability classes|OWASP Top 10 (2021 ed., current 2026)|

## NIST SP 800-61 IR Lifecycle — 4 Phases
1. Preparation
2. Detection and Analysis (scope/impact determined here)
3. Containment, Eradication, and Recovery
4. Post-Incident Activity (lessons learned)

## Containment, Eradication, Recovery — Ordering
| Phase | Goal | Example |
|---|---|---|
|Short-term Containment|Stop spread immediately|VLAN isolation, ACL block, disable account|
|Long-term Containment|Temporary fix while planning full remediation|Emergency patch, firewall rule|
|Eradication|Remove root cause|Delete malware, close backdoor, patch vuln|
|Recovery|Return to normal ops|Restore from clean backup, monitor, re-enable access|

**Exam trap:** Recovery before Eradication reintroduces the threat — always eradicate first.

## Order of Volatility (RFC 3227) — Most to Least Volatile
Registers/Cache → RAM → Temp files → Disk → Remote logs → Physical config → Archival media

## Precursor vs Indicator
- **Precursor** = sign incident MAY occur (future)
- **Indicator** = sign incident IS/HAS occurred (present/past)
