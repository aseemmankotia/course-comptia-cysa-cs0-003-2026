# Answer Key — Practice Test 1

**Q1. Correct: A**

Malware families that use command-and-control resilience techniques often generate hundreds of pseudo-random domain names per day; most fail to resolve (NXDOMAIN) because only the attacker-controlled ones are registered. High-volume NXDOMAIN patterns in DNS logs are the classic indicator analysts use to confirm DGA-based C2 activity.

---

**Q2. Correct: D**

Wireshark provides full packet capture with a GUI, deep protocol dissectors, and a 'Follow TCP Stream' feature that reconstructs an entire conversation payload-by-payload, making it the standard tool for detailed offline packet analysis on the exam.

---

**Q3. Correct: C**

This rule correlates a sequence of related events (multiple failures followed by success) rather than matching a static signature or a known-bad IP/domain. Correlating a behavioral pattern across multiple log events over a time window is the definition of behavior-based correlation used to flag brute-force/credential-stuffing.

---

**Q4. Correct: A**

IOCs are concrete, often perishable artifacts (hashes, IPs, domains, registry keys) tied to a specific incident, whereas TTPs describe how an adversary consistently operates (e.g., spear-phishing delivery, PowerShell-based execution). TTPs are harder for attackers to change and more durable for detection, which is a core CySA+ threat intelligence concept.

---

**Q5. Correct: A**

SPF verifies the sending server is authorized for the claimed domain, and DKIM verifies message integrity via cryptographic signature. Failing both is a strong indicator of a spoofed sender, especially combined with a BEC-style urgent wire-transfer pretext. The correct response is to contain the message (quarantine) and block the malicious sending domain while investigating further.

---

**Q6. Correct: B**

SOAR (Security Orchestration, Automation, and Response) platforms are purpose-built to chain together multiple tools and actions — extracting indicators, submitting them to a sandbox, evaluating verdicts, and automatically enforcing a block — via a defined playbook, directly reducing MTTR for high-volume, low-complexity ticket types like phishing reports.

---

**Q7. Correct: B**

DMARC enforcement happens at the receiving mail server/gateway. If the policy says quarantine but the message lands in the inbox anyway, the receiving gateway simply failed to apply (enforce) the published policy, regardless of the record being correct.

---

**Q8. Correct: B**

Wireshark provides a full GUI for deep packet inspection, TCP stream reconstruction ('Follow TCP Stream'), and dissectors/plugins capable of extracting TLS handshake details and JA3 fingerprints for fingerprinting client/server TLS implementations.

---

**Q9. Correct: A**

T1021 (Remote Services) falls under the Lateral Movement tactic and specifically covers adversaries using valid accounts to log into remote services like RDP, SMB/Windows Admin Shares, and WinRM to move across a network.

---

**Q10. Correct: D**

TTPs describe HOW an adversary operates — their overarching goals (tactics), the methods used to achieve them (techniques), and specific implementation details (procedures). IOCs are discrete, often ephemeral artifacts (hashes, IPs, domains, registry keys) that indicate a specific instance of compromise. TTPs are harder for attackers to change and more valuable for long-term detection than IOCs.

---

**Q11. Correct: D**

Automation refers to a single, repeatable action performed by a system without human intervention — in this case, isolating the host is one automated response action executed directly by the SOAR tool upon trigger.

---

**Q12. Correct: B**

Sinkholing the malicious domain redirects the beacon traffic to a controlled server, allowing the analyst to contain the C2 channel and continue monitoring/logging further attempts from the infected host, all while preserving the compromised system intact for forensic investigation.

---

**Q13. Correct: A**

High-entropy, algorithmically-generated subdomains queried at fixed intervals with low-TTL, rotating IPs are the classic signature of a Domain Generation Algorithm (DGA) used for C2. Analyzing DNS log timing/entropy and enriching with threat intel/passive DNS reputation is the correct analytical technique to confirm malicious beaconing before escalating.

---

**Q14. Correct: B**

Saving the SAM registry hive and dumping LSASS memory with Mimikatz are textbook OS Credential Dumping (T1003) sub-techniques, which MITRE ATT&CK classifies under the Credential Access tactic.

---

**Q15. Correct: C**

Automatically invoking the EDR API to isolate the host and simultaneously opening a ticket is true orchestration — it removes the human bottleneck for containment while still preserving a record for analyst follow-up, directly reducing MTTR.

---

**Q16. Correct: C**

Credentialed scans authenticate to the host, providing accurate patch and configuration data with far fewer false positives than unauthenticated methods. Scheduling during a maintenance window addresses the performance concern.

---

**Q17. Correct: C**

An installed agent scans locally regardless of network reachability and uploads results whenever connectivity to the management server is available, giving continuous visibility on intermittently connected endpoints.

---

**Q18. Correct: B**

AV:N (network), AC:L (low complexity), PR:N (no privileges required), UI:N (no user interaction), combined with C:H/I:H/A:H, describes a remotely exploitable flaw with high impact across all three CIA properties.

---

**Q19. Correct: D**

Effective prioritization uses context awareness beyond raw CVSS: active in-the-wild exploitation combined with a business-critical asset (payment gateway) represents greater real-world risk than a higher base score on a low-value, unexploited system.

---

**Q20. Correct: A**

This describes an Insecure Direct Object Reference (IDOR), a broken access control issue. The root cause is missing per-object authorization validation, which must be enforced server-side on every request.

---

**Q21. Correct: C**

When a patch is unavailable, standard vulnerability response practice is to apply compensating controls to reduce exposure and formally document risk acceptance, satisfying governance requirements until remediation is possible.

---

**Q22. Correct: D**

Agentless, API-integrated scanning queries the orchestration platform and image registry directly, giving continuous coverage of short-lived containers without requiring installation, maintenance, or startup overhead inside every ephemeral instance.

---

**Q23. Correct: D**

Passive scanning listens to traffic already traversing the network via a tap or SPAN port, identifying service banners, protocols, and known vulnerable versions without ever sending a single packet to the sensitive field devices.

---

**Q24. Correct: B**

The Environmental Score is specifically designed to adjust the Base Score based on the organization's real-world context, including compensating controls like segmentation and WAF protection, making it the most accurate representation of actual organizational risk for prioritization purposes.

---

**Q25. Correct: B**

SAST analyzes source code, bytecode, or binaries directly without executing the application, making it the correct choice for catching injection flaws and insecure coding patterns early in the CI pipeline before compilation or deployment.

---

**Q26. Correct: A**

Network segmentation combined with strict access control lists and continuous monitoring is a standard compensating control that reduces exposure and enables detection of exploitation attempts without violating the device's regulatory certification, which prohibits modifying the certified software or OS.

---

**Q27. Correct: A**

Remediation SLAs are risk-based, driven primarily by the vulnerability's severity (CVSS score) and whether a working exploit exists in the wild, since these two factors most directly determine the actual likelihood and impact of exploitation.

---

**Q28. Correct: B**

Agent-based (agentless is the opposite) scanning installs a lightweight agent on each endpoint that performs local assessment and reports results over the internet regardless of network location, solving the coverage gap for remote/roaming devices.

---

**Q29. Correct: C**

When a patch is unavailable and remediation must be delayed, a compensating control (network segmentation/isolation) reduces the exploitability of the vulnerability while the organization works toward a permanent fix, which is standard vulnerability response practice for unpatchable systems.

---

**Q30. Correct: A**

MITRE ATT&CK provides a granular, continuously updated matrix of specific tactics, techniques, and sub-techniques mapped to real-world adversary behavior, making it the best tool for identifying detection coverage gaps at a technique level.

---

**Q31. Correct: A**

The Diamond Model's four core features are exactly adversary, capability, infrastructure, and victim, connected to form an event vertex used for pivoting between related intrusions.

---

**Q32. Correct: A**

Network segmentation/isolation at the switch or firewall is a standard short-term containment strategy that halts lateral movement while preserving volatile evidence and system state for later forensic analysis, and it avoids the operational disruption of shutting down critical clinical systems.

---

**Q33. Correct: D**

Chain of custody documentation must begin the moment evidence is collected, recording every person who handled it, the date/time, and the purpose of each transfer, to prove the evidence has not been tampered with and remains admissible in legal proceedings.

---

**Q34. Correct: C**

A root cause analysis and lessons learned review is the post-incident activity conducted after recovery to determine the underlying cause of control failures and to generate actionable improvements to prevent recurrence.

---

**Q35. Correct: A**

The communication plan within an IR plan defines roles, responsibilities, and protocols for internal and external communications, including who serves as the designated spokesperson for media and regulators to ensure consistent, accurate, and legally compliant messaging.

---

**Q36. Correct: D**

Disabling the network interface (network segmentation/isolation) stops lateral movement and further encryption while keeping the system powered on preserves volatile data such as RAM contents, running processes, and potential encryption keys for forensic analysis.

---

**Q37. Correct: B**

MITRE ATT&CK is a detailed, publicly available matrix of adversary tactics, techniques, and sub-techniques, each mapped to associated detection methods and mitigations, making it ideal for granular technique-level documentation.

---

**Q38. Correct: D**

Per the order of volatility (as outlined in RFC 3227), CPU cache and registers are the most volatile data on a system, being lost almost instantly when power is removed or the process changes state, so they must be captured first.

---

**Q39. Correct: B**

Business and technical constraints (long maintenance windows, vendor support contract restrictions) that prevent timely patching are classic documented 'inhibitors to remediation,' which should be reported along with recommended compensating controls (e.g., network segmentation, enhanced monitoring) until the patch can be applied.

---

**Q40. Correct: C**

Confirmed exposure of PII such as Social Security numbers typically triggers regulatory and contractual breach notification obligations, so legal counsel and the compliance/privacy officer must be looped in immediately to assess notification timelines and legal exposure.

---

**Q41. Correct: C**

Mean time to detect (MTTD) specifically measures the elapsed time from when an intrusion first occurs to when the security team identifies/detects it, making it a key metric in incident response reporting.

---

**Q42. Correct: B**

Executives need audience-appropriate, business-focused reporting: risk trends, financial/operational impact, and prioritized recommendations that support budget and resourcing decisions rather than deep technical detail.

---

**Q43. Correct: D**

The five whys technique is a standard root cause analysis method that iteratively asks 'why' to drill down past the immediate symptom (email bypassed filtering) to the true underlying cause (e.g., misconfigured mail gateway rule).

---

**Q44. Correct: C**

A post-incident meeting held after remediation to review what worked, what didn't, and to update procedures and the incident response plan is the definition of a lessons learned (after-action) review.

---

**Q45. Correct: D**

The vulnerability cannot be patched because the underlying software/hardware is unsupported and effectively end-of-life, with no vendor path forward and prohibitive replacement cost -- this is the textbook definition of the 'legacy systems' inhibitor to remediation used in vulnerability management reporting.

---

**Q46. Correct: C**

A lessons learned report (produced during the post-incident/after-action review) captures process and communication gaps identified during incident handling -- such as escalation delays -- and documents concrete action items to improve future response, which is exactly what's described here.

---

