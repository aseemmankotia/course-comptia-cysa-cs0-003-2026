## Chapter 5: Vulnerability Management: Scanning Methods and Concepts — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Credentialed scan with insufficient/expired admin rights on target — result? | False negatives — the scanner can't authenticate to check real patch levels, so vulnerabilities go undetected. Exam tip: incomplete creds = missed findings, not extra false alarms. |
| 2 | Nmap: host discovery only, no port scan | nmap -sn 192.168.1.0/24 — Exam tip: -sn = ping/discovery scan only (legacy alias -sP). |
| 3 | PCI DSS vulnerability scan frequency requirement | Quarterly (every ~90 days) internal and external scans, plus after any significant network change. Exam tests this exact cadence for scan-scheduling scenarios. |
| 4 | CVSS v3 severity score bands | 0.0 = None, 0.1–3.9 = Low, 4.0–6.9 = Medium, 7.0–8.9 = High, 9.0–10.0 = Critical. Exam maps score ranges to remediation priority. |
| 5 | Active vs passive scanning — key difference | Active sends probes/packets to the target (risk of disruption on fragile systems); passive only observes existing traffic (no packets sent, safe for ICS/SCADA). |
| 6 | Best use case for agent-based scanning | Roaming laptops, remote endpoints, and ephemeral cloud instances/containers — agent reports regardless of network location. Trade-off: deployment and maintenance overhead per host. |
| 7 | Key limitation of agentless scanning | Target must be online, network-reachable, and have accessible ports at scan time — misses hosts offline during the scan window (common with laptops and ephemeral cloud assets). |
| 8 | Best practice for scanning segmented/isolated network zones | Deploy a local scan engine or agent inside each segment instead of opening firewall rules from one central scanner — preserves segmentation and avoids false negatives from blocked ports. |
| 9 | Scanning fragile legacy/ICS systems — recommended method | Use passive scanning, restrict active scans to maintenance windows, or apply a documented scan exclusion with compensating controls (network monitoring). Avoid aggressive active scans that can crash the device. |
| 10 | Nmap credentialed vulnerability scripting example | nmap --script vuln -sV <target> combined with SSH/SMB/WinRM credentials configured in the scanner policy (e.g., Nessus). Credentialed = logs into host to verify patch level directly. |
| 11 | Non-credentialed scan — main advantage vs disadvantage | Advantage: shows the attacker's external view with no credentials to manage or leak. Disadvantage: higher false positive/negative rate; can't verify local patch state or misconfigurations. |
| 12 | Special consideration for scanning ephemeral cloud assets | Short-lived instances/containers may terminate before a scheduled network scan runs. Use agent-based scanning baked into the image, or cloud-native/API-based scanning (CSPM), instead of relying solely on network scans. |
