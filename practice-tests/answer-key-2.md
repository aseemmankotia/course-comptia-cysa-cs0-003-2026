# Answer Key — Practice Test 2

**Q1. Correct: C**

T1047 specifically covers adversary use of WMI for both local and remote execution, and the ATT&CK page lists relevant data sources such as WMI-Activity logs and process command-line auditing, which directly guide the hunt.

---

**Q2. Correct: D**

Passive DNS analysis, when combined with entropy scoring (measuring randomness of the domain string) and checking how recently the domain was registered, is a standard technique for distinguishing algorithmically generated domains used by malware from legitimate high-volume DNS traffic.

---

**Q3. Correct: A**

Adding an allowlist check and multi-source confidence enrichment before the isolation action addresses false positives from stale feed data while preserving the speed benefit of automation - this is the intended design pattern for SOAR playbooks per CySA+ process-improvement objectives.

---

**Q4. Correct: C**

JA3 fingerprints identify client-side TLS negotiation characteristics of specific tooling and are largely independent of the destination IP's reputation; attackers frequently use compromised or newly-provisioned infrastructure with clean reputation. A JA3 match to known C2 tooling should be escalated for endpoint-level investigation regardless of IP reputation.

---

**Q5. Correct: A**

Tokenization substitutes sensitive values with a randomly generated, non-mathematically-related token, with the original value stored separately in a secure vault - there is no key that mathematically derives the original from the token. Encryption instead uses a key-based algorithm that can mathematically reverse the ciphertext back to plaintext.

---

**Q6. Correct: C**

Attackers commonly set the visible display name to match a trusted executive while the actual Return-Path/envelope sender is an unrelated free webmail domain that fails SPF and lacks DKIM signing - a hallmark of display-name spoofing used in BEC attacks, since most mail clients show only the friendly name by default.

---

**Q7. Correct: B**

Event ID 4104 captures the full de-obfuscated content of PowerShell script blocks as they execute, providing direct visibility into the actual commands run — critical for fileless attacks that leave no file artifacts on disk.

---

**Q8. Correct: D**

JA3/JA3S generates a hash fingerprint of the TLS handshake parameters (cipher suites, extensions, etc.), allowing analysts to identify known malware client/server behavior patterns without ever decrypting the payload.

---

**Q9. Correct: D**

Scoping an exception to the known legitimate account while preserving (or refining) the detection logic for all other accounts eliminates the specific false-positive source without weakening overall brute-force detection.

---

**Q10. Correct: D**

DMARC alignment requires the domain that passes SPF/DKIM to match the visible From: header domain. A pass on both but a DMARC alignment failure is a classic pattern of an attacker spoofing a trusted display name while authenticating from a completely different (attacker-controlled) domain.

---

**Q11. Correct: B**

ATT&CK organizes adversary behavior hierarchically: tactics are the high-level goals (e.g., Persistence, Privilege Escalation), and techniques are the specific methods used to accomplish those goals (e.g., T1055 Process Injection).

---

**Q12. Correct: B**

Process injection is an endpoint-level technique in which malicious code is inserted into the memory space of a legitimate running process. Detecting it requires endpoint telemetry that captures process lineage and memory region modifications — data that network or email logs cannot provide.

---

**Q13. Correct: C**

WMI-based remote execution spawns a child process under wmiprvse.exe on the target host. Sysmon Event ID 1 (or Windows Security Event 4688) capturing wmiprvse.exe as the parent of an unexpected process (e.g., cmd.exe or rundll32.exe) is direct, technique-specific evidence of WMI abuse for lateral movement.

---

**Q14. Correct: A**

DNS tunneling is identified by analyzing query characteristics directly — abnormal subdomain length, high entropy (randomness), and unusually high query volume to a single parent domain — then correlating that domain against reputation/threat intel feeds to confirm it is known-malicious or newly registered infrastructure.

---

**Q15. Correct: C**

Best-practice SOAR design automates low-risk, contained actions (quarantining one reported message) for speed, while gating high-impact, organization-wide actions behind human-in-the-loop approval. This preserves efficiency gains while limiting the blast radius of a false positive.

---

**Q16. Correct: D**

CVSS base score alone doesn't account for exploit availability, exposure, or threat intelligence context. Active exploitation combined with internet-facing exposure creates higher real-world risk than a higher base score with no known exploit and internal-only exposure — this is the core principle behind risk-based, context-aware prioritization.

---

**Q17. Correct: C**

Passive scanning observes existing network traffic without sending intrusive probes, avoiding the crash risk in fragile OT/SCADA devices. This is the standard recommended approach for legacy industrial control environments.

---

**Q18. Correct: C**

The Scope (S) metric with value Changed (C) specifically models a vulnerability in one security authority impacting resources governed by a different security authority, such as a VM escape or hypervisor pivot scenario.

---

**Q19. Correct: A**

Deploying, updating, and maintaining agent software across every endpoint is a well-documented operational overhead of agent-based scanning, unlike credentialed network scans which run remotely without requiring endpoint software installation.

---

**Q20. Correct: D**

This describes an Insecure Direct Object Reference (IDOR), a broken access control vulnerability. The correct fix is enforcing server-side object-level authorization checks on every request, rather than relying on obscurity or transport security.

---

**Q21. Correct: C**

When patching is infeasible, standard vulnerability management practice calls for implementing compensating controls to reduce residual risk, combined with formal, documented risk acceptance and appropriate executive approval — satisfying governance requirements while acknowledging the SLA cannot be met as originally defined.

---

**Q22. Correct: A**

Scope Changed means a successful exploit can impact components outside the vulnerable component's own authorization scope (e.g., container or VM escape into the host or hypervisor), dramatically increasing blast radius compared to a scope-unchanged finding with an otherwise identical score.

---

**Q23. Correct: A**

Embedding scanning into the CI/CD pipeline or container image build process catches vulnerabilities before ephemeral workloads ever launch, eliminating the race against a container's short lifespan that plagues traditional network-based scanning.

---

**Q24. Correct: B**

Threat modeling performed during the design phase identifies architectural and design-level security flaws before implementation begins, aligning with the well-established cost curve where earlier detection is dramatically cheaper to remediate.

---

**Q25. Correct: A**

This is an Insecure Direct Object Reference (IDOR), a broken access control weakness. The root cause is a missing object-level authorization check; enforcing server-side verification that the requester is entitled to the specific resource fixes the actual flaw regardless of how the ID is represented.

---

**Q26. Correct: A**

When direct remediation is infeasible, compensating controls such as network segmentation, restrictive ACLs, and enhanced monitoring reduce risk while the exception is formally documented and the remediation SLA is revisited — this is the standard recommended approach for unpatchable critical systems.

---

**Q27. Correct: A**

Effective prioritization combines CVSS severity with contextual exploit intelligence such as EPSS and CISA KEV; a vulnerability under active real-world exploitation represents far greater immediate risk than a high-CVSS finding with negligible exploitation likelihood.

---

**Q28. Correct: C**

CVSS temporal metrics adjust the base score to reflect real-world exploitation likelihood at a point in time. E:H means functional/weaponized exploit code is confirmed to exist, and RC:C means the vulnerability report itself is confirmed — together these indicate Finding A is far more likely to be actively exploited right now, even though the base severity score is the same as Finding B. Effective vulnerability prioritization uses temporal (and environmental) scores layered on top of the base score, not the base score alone.

---

**Q29. Correct: D**

Passive scanning analyzes existing network traffic (protocol behavior, banners, traffic patterns) to identify vulnerable devices and versions without ever sending probe packets to fragile endpoints. This is the standard special-consideration approach for OT/ICS and other environments where active scanning risks operational disruption, as explicitly covered in CySA+ objectives around scan types and special considerations for fragile/legacy systems.

---

**Q30. Correct: B**

The malware's specific technical tooling (the encryption routine/method) is the adversary's 'capability' — the tools, techniques, and malware used to execute the attack.

---

**Q31. Correct: A**

RFC 3227's order of volatility dictates collecting the most fragile data first: CPU registers and cache (nanoseconds), then RAM contents, then disk data, then archival media/backups, since each successive category persists longer without power or active processes.

---

**Q32. Correct: B**

Segmentation/isolation via ACLs blocking SMB traffic stops lateral spread immediately without powering down hosts, preserving RAM and running processes for later forensic analysis — this is a standard short-term containment strategy.

---

**Q33. Correct: D**

The 5 Whys technique involves iteratively asking 'why' a problem occurred, drilling down through causal layers until the true root cause is identified — exactly as described.

---

**Q34. Correct: B**

A tabletop exercise is a discussion-based walkthrough where stakeholders talk through their roles and decisions for a hypothetical scenario without any operational impact — it is the lowest-cost, least disruptive test and typically the first step in an IR/BC-DR testing program.

---

**Q35. Correct: B**

Chain of custody requires that original evidence be secured with strict, documented, and controlled access at all times; storing it in an unlocked closet accessible to unauthorized personnel breaks the chain of custody, creating reasonable doubt about evidence integrity and admissibility.

---

**Q36. Correct: A**

The Diamond Model's four core features are Adversary, Capability, Infrastructure, and Victim. The IP address and the hosting provider used to deliver or control the attack are physical/logical resources the adversary leverages, which the model classifies as Infrastructure.

---

**Q37. Correct: D**

RFC 3227 defines the order of volatility as: (1) registers and cache, (2) routing table, ARP cache, process table, kernel statistics, and memory, (3) temporary file systems, (4) disk, (5) remote logging/monitoring data, (6) physical configuration/network topology, (7) archival media. CPU registers and cache are the single most volatile evidence source and must be captured before any other artifact.

---

**Q38. Correct: B**

Network-based segmentation containment (blocking SMB between VLANs) stops lateral spread immediately without powering down infected hosts, preserving RAM contents for forensic analysis — satisfying both the containment goal and evidence-preservation requirement while allowing unaffected segments to keep functioning.

---

**Q39. Correct: B**

An SLA is a binding contractual agreement with a vendor that defines support terms, including maintenance windows and change scheduling, and is the correct classification when a vendor contract dictates when patching can occur.

---

**Q40. Correct: A**

MTTD measures the elapsed time between when a compromise actually occurs and when the security team identifies it, which is exactly the Day 0-to-Day 12 window described.

---

**Q41. Correct: D**

Board-level stakeholders need business-impact framing, current status, and recovery expectations in plain language to make decisions and speak publicly; deep technical detail is not actionable for this audience.

---

**Q42. Correct: B**

The five whys technique is specifically used in RCA to move past the surface-level technical symptom by repeatedly asking why until the systemic root cause (process, policy, or control failure) is uncovered.

---

**Q43. Correct: D**

When findings remain unresolved, PCI DSS requires documentation of compensating controls and a clear remediation action plan with a timeline so the acquiring bank can assess ongoing risk exposure and compliance intent.

---

**Q44. Correct: C**

A remediation action plan is the operational document that assigns specific vulnerabilities to owners, sets priority, and defines target dates, making it the correct artifact for coordinating tactical patch execution with IT operations.

---

**Q45. Correct: C**

The stated reason for blocking remediation is that patching would halt a critical business process (wire transfer processing) during operational hours -- this is the textbook definition of business process interruption as an inhibitor to remediation, distinct from the approval mechanism used to raise the concern.

---

**Q46. Correct: B**

Root cause analysis is specifically designed to trace an incident back to its underlying systemic or process failure (in this case, an unassigned patch due to a staffing gap) so that organizational leadership can address the root deficiency, such as by allocating additional headcount.

---

