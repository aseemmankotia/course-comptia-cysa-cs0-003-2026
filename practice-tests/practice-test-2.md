# Practice Test 2: CompTIA CySA+ (CS0-003): Complete Analyst Exam Prep

- **Questions:** 46
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-2.md`. Track results in `score-tracker.md`.

---

**Q1.** During a proactive threat hunt, an analyst suspects an adversary is using the Windows Management Instrumentation (WMI) service to execute commands remotely and evade traditional process-creation logging. Which MITRE ATT&CK technique ID should the analyst use to scope the hunt and identify relevant data sources?

A) T1053 - Scheduled Task/Job
B) T1021 - Remote Services
C) T1047 - Windows Management Instrumentation
D) T1055 - Process Injection

---

**Q2.** An analyst notices an internal workstation issuing hundreds of DNS queries per minute for domains with random-looking strings (e.g., xk4j9fh2q.net), most of which return NXDOMAIN. Which technique is BEST suited to confirm this is DGA-based C2 activity rather than benign CDN or ad-network traffic?

A) Reviewing the local hosts file for suspicious static entries
B) Checking the SPF record of the workstation's outbound mail domain
C) Reviewing NetFlow records solely for total bytes transferred per session
D) Passive DNS analysis combined with domain entropy and registration-age scoring

---

**Q3.** A SOAR playbook automatically isolates any endpoint generating an alert that matches a known-malware hash from the threat intel feed. After deployment, several legitimate administrative tools were quarantined because their hashes matched stale entries in the feed. Which playbook modification BEST resolves this without eliminating automation?

A) Add an enrichment step that cross-references the hash against an approved-software allowlist and multiple current threat intel sources before triggering isolation
B) Disable hash-based detection in the playbook entirely
C) Revert to fully manual analyst review for every alert of any severity
D) Increase the overall alert severity threshold required before the playbook can run

---

**Q4.** While reviewing a packet capture, an analyst identifies a TLS ClientHello whose JA3 fingerprint matches known Cobalt Strike beacon tooling, even though the destination IP address has a good reputation score in threat intel platforms. What is the analyst's BEST next step?

A) Dismiss the alert since a good IP reputation score indicates the destination is safe
B) Block only inbound traffic to the host and take no further action
C) Treat the JA3 match as a high-confidence indicator despite the clean IP reputation and escalate for endpoint memory/process investigation
D) Wait until the IP reputation score changes before investigating further

---

**Q5.** Which statement correctly distinguishes tokenization from encryption as data protection methods relevant to SOC data handling practices?

A) Tokenization replaces sensitive data with a non-mathematically-derived surrogate value mapped in a secure token vault, whereas encryption transforms data using a key-based reversible algorithm
B) Tokenization uses the exact same reversible mathematical algorithm and key management process as encryption
C) Encryption always requires less compute overhead at scale than tokenization
D) Tokenization can only be applied to data in transit over a network, never to data at rest

---

**Q6.** A user reports a phishing email appearing to come from the company CEO. Header analysis shows: Return-Path resolves to a free public webmail domain, SPF = fail, DKIM = none, but the friendly "From" display name correctly shows the CEO's full name. What does this combination BEST indicate?

A) SPF failures are typically caused by DNS TTL misconfiguration and can generally be ignored
B) The email is legitimate and was simply forwarded through an approved third-party mail relay
C) Display-name spoofing - the attacker manipulated the friendly "From" field while the underlying sending domain fails authentication, a common Business Email Compromise (BEC) technique
D) DKIM = none confirms the message was digitally signed but not encrypted in transit

---

**Q7.** An analyst suspects a fileless malware attack in which a threat actor is using PowerShell entirely in memory, never writing an executable to disk. Which log source provides the MOST direct evidence of the actual malicious commands executed?

A) Windows Security Event ID 4624 (successful logon)
B) PowerShell Script Block Logging Event ID 4104
C) Sysmon Event ID 3 (network connection)
D) Windows Defender Event ID 1116 (malware detected)

---

**Q8.** A SOC analyst wants to identify malicious C2 traffic hidden within encrypted TLS sessions, without decrypting the traffic or violating data privacy policies. Which technique should be used?

A) NetFlow analysis
B) DNS sinkholing
C) Deep packet inspection with full SSL/TLS decryption
D) JA3/JA3S TLS client and server fingerprinting

---

**Q9.** A SIEM correlation rule alerting on 'more than 3 failed logins within 60 seconds' is generating excessive false positives because a legacy application retries authentication rapidly using a service account. What is the BEST way to tune this rule?

A) Disable the rule entirely
B) Increase the threshold to 100 failed logins in 60 seconds for all accounts
C) Change the rule to only alert on successful logins
D) Add an exception/baseline allowlist for the legitimate service account, and adjust the threshold and time window to reflect genuine brute-force patterns

---

**Q10.** An analyst reviews email headers for a suspected Business Email Compromise attempt. The headers show: SPF: pass (for domain mail-relay.example-billing.com), DKIM: pass (signed by mail-relay.example-billing.com), DMARC: fail — reason 'header.from misalignment.' The visible From: address shows ceo@company.com. What does this indicate?

A) The recipient's mail server is misconfigured
B) The DKIM signature itself is invalid
C) This is a legitimate email and no action is needed
D) The email passed SPF/DKIM checks for a different domain than the visible From: header, indicating likely domain spoofing/impersonation

---

**Q11.** In the MITRE ATT&CK framework, which statement correctly differentiates a 'tactic' from a 'technique'?

A) A technique always maps to exactly one tactic and cannot belong to multiple tactics
B) A tactic represents the adversary's objective or goal (the 'why'); a technique represents the specific method used to achieve that goal (the 'how')
C) Tactics and techniques are interchangeable terms in the framework
D) A tool used by an adversary is called a tactic, while the adversary group itself is called a technique

---

**Q12.** A threat hunter forms a hypothesis that a known APT group, which frequently uses process injection (MITRE ATT&CK T1055), has compromised the environment. Which data source is BEST suited to test this hypothesis?

A) Firewall traffic logs
B) Endpoint process and memory telemetry showing anomalous parent-child process relationships and injected memory regions
C) DNS query logs
D) Email gateway logs

---

**Q13.** A threat hunter is testing the hypothesis that an adversary is using Windows Management Instrumentation (WMI) for remote command execution during lateral movement, consistent with MITRE ATT&CK technique T1047. Which data source provides the STRONGEST evidence to confirm this hypothesis?

A) Windows Event ID 4624 (successful logon) filtered by logon type 3
B) Sysmon Event ID 3 (network connection) logs filtered on destination port 445
C) Sysmon Event ID 1 process creation logs showing wmiprvse.exe as the parent process of an unexpected child process
D) PowerShell Module Logging (Event ID 4103) capturing script block content

---

**Q14.** An analyst reviewing egress traffic notices a large volume of DNS queries to random-looking subdomains of a domain the organization has never used, with average query lengths exceeding 60 characters. Which approach BEST confirms whether this is DNS tunneling used for data exfiltration?

A) Analyze DNS query logs for high-entropy subdomain patterns and correlate the parent domain against threat intelligence domain reputation feeds
B) Perform dynamic sandbox detonation of the IP addresses that the suspicious domain resolves to
C) Capture full packets and inspect only the TLS certificate common name field for the session
D) Review email gateway logs for the sender's SPF alignment results

---

**Q15.** A SOC lead is designing a SOAR playbook to automate response to user-reported phishing emails. Which playbook configuration BEST balances automation efficiency with risk of business disruption?

A) Automatically delete the reported email from all mailboxes and block the sender domain organization-wide without any review
B) Disable the SOAR playbook and route every reported phishing email to a Tier 3 analyst for full manual investigation
C) Auto-quarantine the single reported message immediately, but require analyst approval before executing organization-wide actions such as domain blocking or mailbox-wide purges
D) Configure the playbook to automatically close the incident ticket after 24 hours regardless of analyst response

---

**Q16.** A vulnerability management program identifies two findings: Finding A has a CVSS v3.1 base score of 9.8 (AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H) affecting an internal database server with no known public exploit code. Finding B has a CVSS v3.1 base score of 7.5 affecting an internet-facing web application, and threat intelligence confirms active weaponized exploitation in the wild targeting this exact CVE. Given limited remediation resources this cycle, which finding should be prioritized FIRST?

A) Finding A, because its CVSS score of 9.8 is higher and therefore represents greater risk
B) Both findings equally, since CVSS scores above 7.0 require identical remediation timelines under most SLAs
C) Neither should be prioritized until a formal risk assessment board approves the remediation budget
D) Finding B, because active weaponized exploitation and internet exposure increase real-world risk beyond what the base CVSS score reflects

---

**Q17.** A security analyst must assess vulnerabilities on a network segment containing legacy SCADA controllers that are known to crash or hang when receiving unexpected packets during active scans. Which vulnerability assessment approach is MOST appropriate for this environment?

A) Non-credentialed active scanning during a scheduled maintenance window
B) Agent-based scanning installed directly on each SCADA controller
C) Passive network monitoring/scanning that analyzes traffic without sending probes to the devices
D) Credentialed active scanning using the vendor's default administrative account

---

**Q18.** An analyst is reviewing a CVSS v3.1 vector string and needs to determine whether a successful exploit could allow an attacker to affect resources outside the vulnerable component itself, such as pivoting from a hypervisor to affect guest VMs. Which base metric and value combination indicates this condition?

A) C:H (Confidentiality Impact: High)
B) AV:N (Attack Vector: Network)
C) S:C (Scope: Changed)
D) PR:N (Privileges Required: None)

---

**Q19.** Which statement BEST describes a key limitation of agent-based vulnerability scanning compared to credentialed network scanning?

A) Agent-based scanning requires software to be deployed and maintained on every target endpoint, increasing management overhead
B) Agent-based scanning cannot detect missing patches on the host it is installed on
C) Agent-based scanning always requires the target device to be connected to the corporate network during the scan
D) Agent-based scanning cannot provide any configuration or compliance data about the host

---

**Q20.** A web application vulnerability scan reports that authenticated users can modify the numeric 'account_id' parameter in a URL to view or edit other customers' order records without authorization. Which control BEST remediates this specific vulnerability class?

A) Encrypt the account_id parameter value using TLS in transit
B) Require multifactor authentication for all user logins
C) Implement input validation to reject account_id values containing special characters
D) Enforce server-side authorization checks that verify the requesting user owns or has rights to the referenced account_id on every request

---

**Q21.** A vulnerability scan identifies a critical CVE on a legacy manufacturing control system. The vendor has confirmed no patch will ever be released because the system is end-of-life, and replacing it is not feasible for 18 months due to budget cycles. The organization's patching SLA requires critical vulnerabilities to be remediated within 15 days. Which action is MOST appropriate?

A) Decommission the system immediately regardless of the operational impact to stay within SLA
B) Accept the risk formally and take no further action since a patch is not available
C) Implement compensating controls (e.g., network segmentation, strict access control, enhanced monitoring) and document formal risk acceptance with executive sign-off for the SLA exception
D) Ignore the SLA breach since the vendor is at fault for not releasing a patch

---

**Q22.** An analyst reviews a vulnerability scan report showing a CVSS v3.1 vector of AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H for a finding on an API gateway. Which factor in this vector should MOST influence the analyst to escalate remediation ahead of a similarly scored vulnerability with S:U (Scope Unchanged)?

A) The Scope Changed (S:C) metric, indicating the vulnerability can affect resources beyond its own security scope
B) The Attack Complexity rating of Low
C) The Availability impact rating of High
D) The User Interaction requirement of None

---

**Q23.** A security team manages an environment with thousands of short-lived containers that spin up and terminate within minutes as part of a CI/CD pipeline. Traditional network-based credentialed scans miss most of these instances because they terminate before a scan cycle completes. Which vulnerability detection approach BEST addresses this gap?

A) Deploy an agent-based/embedded scanner that inspects the container base image at build time and reports at runtime
B) Increase the frequency of non-credentialed network scans to catch containers faster
C) Schedule credentialed scans to run continuously against the container orchestration platform's IP range
D) Switch to passive network traffic analysis to infer vulnerabilities from packet captures

---

**Q24.** During which phase of the secure software development lifecycle (SSDLC) should threat modeling be performed to have the greatest impact on reducing the cost of remediating design-level security flaws?

A) During user acceptance testing, immediately before production release
B) During the design phase, before code is written
C) During the maintenance phase, after the application has been in production for six months
D) During the requirements-gathering phase only, without revisiting after architecture changes

---

**Q25.** A vulnerability scan flags a REST API endpoint that allows a user to retrieve any customer's invoice by simply changing the numeric invoice ID in the URL, with no verification that the requesting user is entitled to that invoice. Which control BEST remediates this finding?

A) Implement server-side authorization checks that verify the requesting user owns or is entitled to the requested invoice ID
B) Encrypt the invoice ID values using AES-256 before transmitting them in the URL
C) Add rate limiting to the endpoint to prevent automated enumeration of invoice IDs
D) Require HTTPS with TLS 1.2 or higher for all API traffic to this endpoint

---

**Q26.** A critical vulnerability (CVSS 9.8) is identified on a legacy SCADA controller that cannot be patched without voiding the manufacturer's warranty and halting a revenue-generating production line. The vendor states a patch will not be available for at least 12 months. Which action represents the BEST immediate response consistent with vulnerability management best practices?

A) Isolate the controller on a segmented network with strict ACLs and monitoring as a compensating control, documenting the exception and revisiting the SLA timeline
B) Decommission the SCADA controller immediately to eliminate the vulnerability
C) Formally accept the risk and take no further action until the vendor releases a patch
D) Apply the patch anyway despite the warranty risk because the CVSS score exceeds the organization's critical threshold

---

**Q27.** A vulnerability scan report lists two findings: Finding A has a CVSS base score of 9.1 but an EPSS score of 0.02 (2% probability of exploitation in the next 30 days) and no known public exploit. Finding B has a CVSS base score of 7.4, an EPSS score of 0.89 (89% probability), and appears on CISA's Known Exploited Vulnerabilities (KEV) catalog. Given limited remediation resources this week, which finding should the analyst prioritize FIRST?

A) Finding B, because real-world exploitability data (EPSS and active exploitation) indicates significantly higher immediate risk despite the lower CVSS score
B) Both findings equally, since remediation SLAs are based only on severity rating regardless of exploit data
C) Neither finding, until asset criticality data is gathered for both systems
D) Finding A, because CVSS base score is the industry-standard sole metric for prioritization

---

**Q28.** A vulnerability management analyst reviews two findings with identical CVSS v3.1 base scores of 8.8 (High), both affecting internet-facing assets of equal business value. Finding A has temporal metrics E:H/RL:O/RC:C (Exploit Code Maturity: High, Remediation Level: Official Fix, Report Confidence: Confirmed). Finding B has E:U/RL:U/RC:U (Unproven, Unavailable, Unconfirmed). Which finding should be prioritized for immediate remediation?

A) Finding B, because the unconfirmed report requires urgent verification work before remediation can even begin
B) Neither should be prioritized over the other — since base scores are identical, remediation SLAs should treat them the same regardless of temporal metrics
C) Finding A, because confirmed reporting and existing weaponized exploit code substantially increase near-term exploitation likelihood despite equal base severity
D) Finding B, because the lack of an official patch (RL:U) means it is less exposed to automated scanning tools

---

**Q29.** A security team must maintain ongoing vulnerability visibility on a manufacturing plant's SCADA/ICS network composed of legacy programmable logic controllers (PLCs) that are known to crash or halt physical processes when subjected to active network probing. Management requires continuous risk visibility without disrupting production. Which scanning approach BEST fits this environment?

A) Schedule authenticated active scans during off-peak production hours to minimize operational impact
B) Install lightweight vulnerability scanning agents directly on each PLC for continuous local assessment
C) Perform non-credentialed active scans only, since removing credentials reduces the risk of crashing the PLCs
D) Deploy passive network traffic monitoring to identify vulnerabilities and indicators of exposure without sending probes to the devices

---

**Q30.** During a Diamond Model analysis of an intrusion, an analyst maps four core features of the event. The malware sample uses a custom RC4-based encryption routine with a hardcoded key that has been seen in three prior campaigns attributed to the same threat actor. Which Diamond Model feature does this custom encryption routine represent?

A) Victim
B) Capability
C) Infrastructure
D) Adversary

---

**Q31.** A forensic analyst arrives at a compromised server that is still powered on and must collect evidence following the correct order of volatility. Which sequence is correct, from MOST volatile to LEAST volatile?

A) CPU registers/cache, RAM contents, disk data, archival media/backups
B) Disk data, archival media, CPU registers and cache
C) Archival media, disk data, RAM contents
D) RAM contents, archival media, disk data, CPU registers

---

**Q32.** Ransomware is actively encrypting files across multiple hosts on a flat network segment via SMB (port 445). The incident commander needs to stop the spread immediately while preserving the ability to investigate infected hosts. Which containment action is BEST?

A) Power off all affected hosts immediately to stop encryption
B) Disable SMB (port 445) at the network segment's firewall/switch ACLs to isolate affected hosts while keeping them powered on
C) Run a full antivirus scan on all hosts on the segment before taking any network action
D) Wait until the eradication phase to take any containment action, since containment could destroy volatile evidence

---

**Q33.** During post-incident review, an analyst wants to identify the underlying root cause of a breach by repeatedly asking 'why' a failure occurred until reaching the fundamental cause, rather than mapping all contributing categories of failure (people, process, technology, environment) visually. Which root cause analysis technique is being used?

A) Fishbone (Ishikawa) diagram
B) MITRE ATT&CK Navigator
C) Business Impact Analysis
D) 5 Whys technique

---

**Q34.** An organization's IR plan has never been tested. Leadership wants a low-cost, low-disruption exercise where key stakeholders discuss their roles and responses to a hypothetical incident scenario in a conference room, without touching production systems. Which type of IR plan test should be conducted FIRST?

A) Full-scale/live exercise involving actual system failover
B) Tabletop exercise
C) Parallel test running the DR site alongside production
D) Simulation test with live but isolated systems

---

**Q35.** A junior analyst collects a hard drive from a compromised workstation, images it, and stores the original drive in an unlocked supply closet accessible to the whole IT team while working on the image. Legal counsel later says the evidence may be inadmissible. What is the MOST likely reason?

A) The image was taken using a write blocker, which is not forensically valid
B) The chain of custody was broken because the original evidence was not secured in a controlled, access-restricted location
C) Hashing was not performed on the image before analysis began
D) The analyst should have used the image instead of the original drive for storage, and vice versa

---

**Q36.** During an incident investigation, an analyst determines that malware on a compromised endpoint communicates with command-and-control infrastructure hosted at IP address 203.0.113.50, which is registered to a known bulletproof hosting provider. Using the Diamond Model of Intrusion Analysis, this IP address and hosting provider represent which core feature of the event?

A) Infrastructure
B) Adversary
C) Victim
D) Capability

---

**Q37.** An analyst begins live forensic collection on a compromised Linux production server that remains powered on and actively processing traffic. Per RFC 3227's standard order of volatility, which of the following artifacts should be collected FIRST, before all others?

A) Contents of the ARP cache and routing table
B) Contents of physical memory (RAM)
C) Temporary file system contents (e.g., /tmp)
D) CPU register and cache contents

---

**Q38.** A CySA+ incident response team detects active ransomware encrypting files and spreading laterally via SMB (port 445) across multiple VLANs in a segmented enterprise network. The team must halt further propagation while preserving volatile memory evidence on infected hosts for later forensic analysis, and without disrupting business operations on unaffected segments. Which containment action BEST meets these requirements?

A) Immediately power off every affected server to stop the encryption process
B) Block SMB (port 445) traffic at the firewall/ACL between affected and unaffected VLANs while leaving infected systems running for memory capture
C) Restore all affected systems from last night's backup immediately
D) Disconnect the entire enterprise network from the internet until the incident is resolved

---

**Q39.** A vulnerability management team identifies a critical CVE affecting an ICS controller in a manufacturing plant. The third-party vendor's support contract states that any firmware update must be scheduled through the vendor and can only occur during a bi-annual maintenance window, delaying remediation by four months. Which of the following BEST describes this remediation inhibitor?

A) Business process interruption caused by patch installation
B) Service level agreement (SLA) restricting patch windows
C) Lack of an available proof-of-concept exploit
D) Memorandum of understanding (MOU) outlining data ownership responsibilities

---

**Q40.** An incident timeline reconstruction shows an attacker gained initial access to a workstation on Day 0, but the SOC did not identify anomalous C2 beaconing until Day 12. Which metric captures this Day 0-to-Day 12 gap?

A) Mean time to detect (MTTD)
B) Mean time to respond (MTTR)
C) Mean time to contain (MTTC)
D) Mean time to recover (MTTRc)

---

**Q41.** During a ransomware incident affecting a hospital's patient scheduling system, the CISO must brief the board of directors 30 minutes before a scheduled press conference. Which report characteristic is MOST appropriate for this audience?

A) A packet capture summary showing the exact exploit signature used against the domain controller
B) A raw IOC list formatted in STIX/TAXII for external threat intel sharing
C) The complete technical incident response playbook used by the SOC team
D) A high-level summary of business impact, containment status, and estimated recovery timeline, free of technical jargon

---

**Q42.** When drafting a root cause analysis (RCA) report following a data breach, which technique/section is used to iteratively ask 'why' a failure occurred until the systemic, underlying cause is identified, rather than stopping at the technical symptom?

A) Chain of custody documentation
B) Five whys analysis
C) Impact assessment section
D) Indicator of compromise (IOC) summary

---

**Q43.** A retail organization must submit quarterly vulnerability scan results to maintain PCI DSS compliance. The latest scan found three high-severity vulnerabilities on a point-of-sale system, and remediation is still pending a scheduled patch cycle. Which document is required to explain the outstanding findings and remediation timeline to the acquiring bank?

A) An Attestation of Compliance (AOC) stating no exceptions were found
B) A Self-Assessment Questionnaire (SAQ) submitted without supporting documentation
C) A Report on Compliance (ROC) that omits the vulnerability details
D) A compensating controls worksheet with a documented remediation action plan and timeline

---

**Q44.** A vulnerability management program lead needs to communicate to IT operations managers exactly which systems require patching, the assigned system owner, the priority ranking, and the target completion date for the next patch cycle. Which document BEST fits this purpose?

A) Executive risk summary
B) Compliance attestation letter
C) Remediation action plan
D) Organizational risk register

---

**Q45.** A financial services firm's vulnerability management team flags a critical CVE on a legacy application that processes wire transfers. The team requests emergency patching, but the change advisory board denies the request, citing that applying the patch requires a 6-hour system outage that would halt wire transfer processing during business hours, causing significant operational and customer impact. Which inhibitor to remediation does this scenario BEST represent?

A) Organizational governance restriction
B) Proof-of-concept exploit unavailability
C) Business process interruption
D) Memorandum of understanding (MOU) constraint

---

**Q46.** Following containment of a data breach caused by an unpatched VPN appliance, the post-incident review reveals that the vulnerability had been identified by the vulnerability management team eight months earlier but was never assigned or remediated due to a staffing gap in the patching team. Leadership requests a document that specifically identifies this underlying systemic failure to justify a budget request for additional vulnerability management headcount. Which report type BEST fulfills this specific purpose?

A) Lessons learned report
B) Root cause analysis
C) Chain of custody documentation
D) Executive briefing summary

---

