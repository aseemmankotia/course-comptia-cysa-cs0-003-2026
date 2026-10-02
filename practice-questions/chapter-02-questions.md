## Chapter 2: Security Operations: Detecting Malicious Activity with SIEM, Logs, and Packet Data — Practice Questions

**Q1.** A SOC analyst reviewing SIEM logs notices a workstation making outbound connections to the same external IP every 45 seconds, each connection transferring nearly identical packet sizes over port 8443 to a domain registered two days ago. What does this MOST likely indicate?

A) Normal NTP time synchronization traffic
B) A legitimate software vendor update check-in
C) A DNS zone transfer between authoritative servers
D) Malware beaconing to a command-and-control (C2) server

<details>
<summary>Answer</summary>

**Correct: D**

Fixed-interval connections, consistent packet size, a non-standard/encrypted port, and a newly registered domain are the classic signature of C2 beaconing.

**Why the others are wrong:**
- NTP uses UDP port 123 and tiny fixed-size packets, not port 8443 with data-bearing payloads.
- Update check-ins typically go to known vendor domains with established reputation, not domains registered days ago.
- Zone transfers occur over TCP 53 between DNS servers, not from a workstation to an unrelated external IP.

</details>

---

**Q2.** An analyst finds that a user's endpoint has a new entry in HKCU\Software\Microsoft\Windows\CurrentVersion\Run pointing to an unsigned executable in the user's temp folder, and this process spawned PowerShell with an encoded command shortly after a Word document was opened. Which category of indicator is this?

A) Network-based indicator
B) Application-layer indicator (SQLi/XSS)
C) Host-based indicator of persistence and malicious execution chain
D) Social-engineering indicator

<details>
<summary>Answer</summary>

**Correct: C**

Registry Run key modification is a classic persistence mechanism, and an Office app spawning PowerShell is a well-known host-based malicious execution chain (living-off-the-land technique).

**Why the others are wrong:**
- No network traffic pattern was described; this is entirely local to the endpoint.
- SQLi/XSS indicators appear in web application/server logs, not registry keys or process trees.
- The initial phishing delivery may be social engineering, but the evidence described (registry, process chain) is host-based, not the lure itself.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A web server access log contains the following request: GET /product.php?id=1' UNION SELECT username,password FROM users-- HTTP/1.1. What attack does this log entry represent?

A) UNION-based SQL injection
B) Cross-site scripting (XSS)
C) Cross-site request forgery (CSRF)
D) Directory traversal

<details>
<summary>Answer</summary>

**Correct: A**

The UNION SELECT syntax combined with a comment terminator (--) is a textbook UNION-based SQL injection attempting to extract data from the users table.

**Why the others are wrong:**
- XSS injects script tags or JavaScript event handlers into input fields, not SQL syntax.
- CSRF exploits authenticated session trust via forged requests and leaves no SQL syntax in the URL.
- Directory traversal uses sequences like ../../etc/passwd, not SQL keywords.

</details>

---

**Q4.** An analyst suspects a host is exfiltrating data via DNS tunneling. Which Wireshark display filter would BEST help identify this activity?

A) dns && frame.len > 100
B) tcp.flags.syn==1 && tcp.flags.ack==0
C) http.request.method=="POST"
D) icmp.type==8

<details>
<summary>Answer</summary>

**Correct: A**

DNS tunneling encodes exfiltrated data into unusually large DNS query/response payloads, so filtering for large DNS frames helps surface abnormal queries for further inspection.

**Why the others are wrong:**
- This filter isolates SYN-only packets, which identifies port scanning, not DNS tunneling.
- This filter targets HTTP POST requests, relevant to web-based exfiltration, not DNS-based.
- This filter shows ICMP echo requests, relevant to ping sweeps, not DNS tunneling.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** An analyst needs to determine the runtime behavior of a suspicious executable — including files it creates, registry keys it modifies, and network connections it attempts — without risking the production environment. Which tool is BEST suited for this task?

A) VirusTotal hash lookup
B) Cuckoo Sandbox dynamic analysis
C) Wireshark packet capture
D) Nessus vulnerability scanner

<details>
<summary>Answer</summary>

**Correct: B**

Cuckoo Sandbox executes the file in an isolated virtual environment and reports full behavioral telemetry (file, registry, and network activity), which is dynamic analysis.

**Why the others are wrong:**
- A VirusTotal hash lookup is static/reputation-based and does not execute the file to observe behavior.
- Wireshark captures network traffic but does not execute or observe host-level behavior of the file.
- Nessus scans for vulnerabilities in systems; it does not perform malware behavioral analysis.

</details>

---

**Q6.** An analyst wants to configure a SIEM correlation rule to detect password spraying while minimizing false positives from routine account lockouts. Which threshold configuration is BEST?

A) Alert on 1-3 failed logins across 50+ distinct accounts from the same source IP within 10 minutes
B) Alert on 10+ failed logins against a single account within 5 minutes
C) Alert on any single failed login attempt regardless of account or source
D) Alert on 1 failed login per account per day, aggregated weekly

<details>
<summary>Answer</summary>

**Correct: A**

Password spraying uses a small number of attempts per account across many accounts to stay under per-account lockout thresholds, so the rule must correlate low attempt counts across a large account population from one source.

**Why the others are wrong:**
- This threshold pattern detects brute force against one account, not spraying across many accounts.
- Alerting on every single failed login generates excessive false positives and is not a correlation rule.
- A weekly aggregation window is too slow to detect an active spraying campaign and would delay response.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which BPF capture filter correctly captures only traffic to or from host 10.0.0.5 on TCP port 443 as it is written to a live capture in Wireshark or tcpdump?

A) ip.addr==10.0.0.5 && tcp.port==443
B) host==10.0.0.5 port=443
C) src 10.0.0.5 or dst 443
D) host 10.0.0.5 and tcp port 443

<details>
<summary>Answer</summary>

**Correct: D**

BPF capture filter syntax uses keywords like host, port, and and/or, applied before packets are captured; this is distinct from Wireshark display filter syntax.

**Why the others are wrong:**
- This is valid Wireshark display filter syntax (ip.addr==, tcp.port==) but is invalid for a live capture filter.
- This syntax mixes invalid operators; BPF does not use == or = signs.
- This filter is malformed and logically incorrect — dst 443 is not a valid port comparison without the 'port' keyword, and the 'or' logic would not restrict to a single host+port pair.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which of the following BEST distinguishes a host-based indicator of compromise from a network-based indicator?

A) Host-based indicators involve traffic patterns between systems; network-based indicators involve file system changes
B) There is no meaningful distinction; the terms are interchangeable on the exam
C) Host-based indicators can only be detected by antivirus; network-based indicators can only be detected by a SIEM
D) Host-based indicators are observed on the endpoint itself, such as registry modifications and unauthorized processes, while network-based indicators are observed in traffic, such as beaconing and port scans

<details>
<summary>Answer</summary>

**Correct: D**

Host-based IOCs (registry keys, unauthorized processes, file hashes) live on the endpoint; network-based IOCs (beaconing intervals, scan patterns, unusual DNS queries) are observed in traffic between systems.

**Why the others are wrong:**
- This reverses the definitions — traffic patterns are network-based, not host-based.
- The exam explicitly tests the ability to distinguish these categories; they are not interchangeable.
- Detection tooling overlaps significantly (e.g., a SIEM can ingest EDR/host telemetry); the distinction is about where the indicator originates, not which single tool can see it.

</details>

---

