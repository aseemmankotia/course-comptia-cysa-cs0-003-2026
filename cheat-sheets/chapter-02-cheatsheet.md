# Security Operations Cheat Sheet (CS0-003 Domain 1 — 33%)

## Indicator Categories
| Type | Examples | Where Found |
|---|---|---|
| Network | Beaconing (fixed intervals), port/vuln scanning, DDoS traffic spikes | Packet captures, NetFlow, firewall/IDS logs |
| Host | Unauthorized processes, Run key/registry changes, new services, scheduled tasks | EDR, Sysmon, Windows Event Logs |
| Application | SQLi (UNION SELECT, --), XSS (`<script>`, onerror=), abnormal HTTP verbs | Web/app server logs, WAF logs |
| Social Engineering | Spoofed sender domains, SPF/DKIM/DMARC failures, urgency language, mismatched Reply-To | Email headers, phishing reports |

## Wireshark: Capture vs Display Filters
| Filter Type | Syntax Example | Notes |
|---|---|---|
| Capture (BPF) | `host 10.0.0.5 and tcp port 443` | Set BEFORE capture; unmatched packets are permanently dropped |
| Display | `ip.addr==10.0.0.5 && tcp.port==443` | Applied AFTER capture; can be changed anytime |
| SYN scan detect | `tcp.flags.syn==1 && tcp.flags.ack==0` | Half-open/stealth scan |
| Large DNS frames | `dns && frame.len > 100` | Possible DNS tunneling |
| POST exfil check | `http.request.method=="POST"` | HTTP-based exfiltration |

## SIEM Correlation Rule Patterns
| Attack | Rule Pattern |
|---|---|
| Brute force | Many failed logins, ONE account, short window |
| Password spraying | Few failed logins (1-3), MANY accounts (50+), ONE source IP, 10-15 min window |
| Impossible travel | Same account, logins from geographically distant locations within impossible timeframe |
| Beaconing | Fixed-interval outbound connections, low jitter, consistent packet size, to low-reputation/new domain |

## Email/Phishing Header Analysis
| Mechanism | Purpose |
|---|---|
| SPF | Validates sending IP is authorized for domain |
| DKIM | Cryptographic signature validates message wasn't altered |
| DMARC | Policy enforcement (none/quarantine/reject) using SPF + DKIM |
| Received headers | Trace actual sending path; check for domain spoofing/mismatch with From: |

## Malware Triage & Sandboxing
| Method | Tool Example | Reveals |
|---|---|---|
| Static analysis | VirusTotal, strings, hash lookup | Known signatures, file metadata — no execution |
| Dynamic analysis | Cuckoo Sandbox | Runtime file/registry/network behavior in isolated VM |
| Network analysis | Wireshark | Traffic patterns, C2 callbacks, protocol anomalies |

## Common Exam Traps
- BPF capture filter syntax ≠ Wireshark display filter syntax (`host X and port Y` vs `ip.addr==X && tcp.port==Y`).
- Password spraying ≠ brute force — spraying spreads FEW attempts across MANY accounts.
- Beaconing detection relies on **periodicity/jitter**, not just connection volume.
- SPF/DKIM/DMARC are three DISTINCT mechanisms — exam tests telling them apart.
- Static analysis never executes the file; only dynamic/sandbox analysis reveals runtime behavior.
