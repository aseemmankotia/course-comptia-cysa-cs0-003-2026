## Chapter 5 Cheat Sheet — Scanning Methods & Concepts

### Credentialed vs Non-Credentialed
| Aspect | Credentialed | Non-Credentialed |
|---|---|---|
| Access | Logs in (SSH/SMB/WinRM) | Remote fingerprinting only |
| Accuracy | High — checks real patch level | Lower — infers from banners |
| False positives/negatives | Low | Higher |
| Risk | Credential exposure/leakage | None (no creds used) |
| Exam trap | Bad creds → false NEGATIVES, not positives | Non-cred good for external attacker view |

### Active vs Passive Scanning
| Aspect | Active | Passive |
|---|---|---|
| Method | Sends probes/packets | Observes existing traffic (TAP/SPAN) |
| Risk to target | Can crash fragile systems | Zero risk — no packets sent |
| Coverage | Full port/service enumeration | Only sees traffic that occurs |
| Best for | Standard IT assets | ICS/SCADA, fragile/legacy devices |

### Agent-Based vs Agentless
| Aspect | Agent-Based | Agentless |
|---|---|---|
| Requires software on host | Yes | No |
| Works off-network/roaming | Yes | No — needs reachability |
| Ephemeral cloud/containers | Ideal (bake into image) | Misses short-lived instances |
| Overhead | Deployment/patch mgmt per host | None on host, but scan-time network load |

### Special Scan Considerations
- **Segmented networks**: deploy local scan engines/agents per segment — don't punch firewall holes for a central scanner.
- **ICS/SCADA & fragile/legacy/medical devices**: prefer passive scanning; if active is required, restrict to maintenance windows or exclude with compensating controls (documentation, network monitoring).
- **Cloud assets**: use agent-in-image or cloud-provider API/CSPM scanning for ephemeral instances that may not exist during a scheduled network scan.
- **Critical/production systems**: throttle scan speed, stagger schedules across maintenance windows to reduce CPU/network impact.

### Scan Scheduling Numbers
- PCI DSS: quarterly internal/external scans (~90 days) + after significant changes.
- CVSS bands: None 0.0 | Low 0.1–3.9 | Medium 4.0–6.9 | High 7.0–8.9 | Critical 9.0–10.0.

### Common Nmap Commands
| Purpose | Command |
|---|---|
| Discovery only (no ports) | `nmap -sn <range>` |
| Vulnerability scripts | `nmap --script vuln -sV <target>` |
| Full port scan | `nmap -p- <target>` |

### Exam Gotchas
1. Fragile system in scenario → answer is passive scanning or scan exclusion, never "aggressive active scan."
2. Segmentation scenario → answer is distributed scan engines/agents, not opening firewall rules.
3. Ephemeral/cloud scenario → answer is agent-based or API/CSPM scanning, not scheduled network scans.
