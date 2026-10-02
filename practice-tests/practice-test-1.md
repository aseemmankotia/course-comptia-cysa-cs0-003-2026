# Practice Test 1: CompTIA CySA+ (CS0-003): Complete Analyst Exam Prep

- **Questions:** 46
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-1.md`. Track results in `score-tracker.md`.

---

**Q1.** During threat hunting, a SOC analyst discovers a workstation generating hundreds of DNS queries per minute to seemingly random, algorithmically generated domain names, with most queries returning NXDOMAIN. Which conclusion BEST explains this observation?

A) Domain Generation Algorithm (DGA) activity confirmed via DNS log analysis showing a high volume of NXDOMAIN responses to algorithmically generated names
B) ARP spoofing detected via network flow analysis
C) DNS tunneling detected via NetFlow analysis alone
D) Typosquatting detected via a manual WHOIS lookup

---

**Q2.** An analyst needs to capture full packet payloads on a network segment and reconstruct an entire TCP conversation for offline protocol-level review of a suspected data exfiltration attempt. Which tool is BEST suited for this task?

A) tcpdump run interactively at the command line without stream reassembly
B) Zeek, which primarily generates connection and protocol summary logs rather than full payload capture
C) Nmap, a network and port scanning utility
D) Wireshark, which captures packets with protocol dissection and TCP stream reassembly for full conversation review

---

**Q3.** A SOC configures a SIEM rule that only triggers an alert when it observes five failed login attempts from the same source IP within two minutes, immediately followed by one successful login. Which detection technique does this rule represent?

A) Signature-based detection matching a known exploit byte pattern
B) Reputation-based detection using an external threat intelligence feed
C) Behavior-based correlation combining repeated authentication failures with a subsequent success, indicative of brute-force or credential-stuffing activity
D) Anomaly-based detection using statistical baseline deviation

---

**Q4.** Which statement BEST distinguishes an Indicator of Compromise (IOC) from a Tactic, Technique, and Procedure (TTP) in threat intelligence analysis?

A) An IOC is a forensic artifact evidencing a specific intrusion (e.g., a file hash, malicious IP, or domain), while a TTP describes the behavioral pattern an adversary consistently uses across campaigns
B) An IOC describes the adversary's behavior patterns while a TTP is a static forensic artifact
C) IOC and TTP are interchangeable terms referring to the same underlying concept
D) A TTP applies only to insider threat activity while an IOC applies only to external attackers

---

**Q5.** A user reports a suspicious email appearing to come from the company's CFO requesting an urgent wire transfer. The analyst reviews the email headers and finds 'Received-SPF: fail' and 'DKIM=fail'. Which conclusion and action is BEST supported by this evidence?

A) The message failed both SPF and DKIM authentication, strongly indicating spoofing; the analyst should quarantine the message and block the sending domain pending further investigation
B) The SPF failure is likely a false positive from a misconfigured internal mail relay and can be safely ignored
C) A DKIM failure only indicates a message formatting issue and does not affect authenticity assessment
D) The email should be treated as legitimate since DMARC alignment was not explicitly evaluated in the headers

---

**Q6.** A SOC wants to reduce mean time to respond (MTTR) for phishing report tickets by automatically extracting URLs and file hashes from reported emails, submitting them to a sandbox, and blocking confirmed malicious indicators at the email gateway without analyst intervention for low-risk cases. Which capability BEST supports this workflow?

A) SIEM log aggregation and dashboarding alone
B) SOAR playbook automation to orchestrate indicator extraction, sandbox submission, and automated blocking for confirmed low-risk threats
C) Manual runbook execution requiring tier-1 analyst review of every ticket
D) Vulnerability scanner integration focused on patch management prioritization

---

**Q7.** A SOC analyst receives a reported phishing email. The email headers show: SPF: pass, DKIM: fail, DMARC: fail (p=quarantine). Despite the domain's DMARC policy specifying quarantine, the message was delivered directly to the user's inbox. Which of the following BEST explains this behavior?

A) The DMARC record's alignment mode allows partial matches by default, causing DKIM failures to still pass
B) The email gateway did not enforce the DMARC policy published in the sending domain's DNS record
C) SPF passing is sufficient by itself to allow delivery regardless of DKIM or DMARC results
D) The DMARC p=quarantine policy only applies to fraudulent top-level domains, not spoofed subdomains

---

**Q8.** An analyst needs to perform deep protocol analysis of a suspected C2 beacon captured in a PCAP file, including reconstructing TCP streams and inspecting TLS handshake metadata such as JA3 fingerprints. Which tool is BEST suited for this task?

A) tcpdump
B) Wireshark
C) Nmap
D) Netcat

---

**Q9.** During a proactive threat hunt, an analyst wants to search for evidence of lateral movement performed using stolen credentials against remote administrative services (e.g., RDP, SMB, WinRM). Which MITRE ATT&CK technique should the hunt focus on?

A) T1021 - Remote Services
B) T1071 - Application Layer Protocol
C) T1583 - Acquire Infrastructure
D) T1059 - Command and Scripting Interpreter

---

**Q10.** Which of the following BEST differentiates a Tactic, Technique, and Procedure (TTP) from an Indicator of Compromise (IOC)?

A) An IOC describes long-term adversary behavior patterns, while a TTP is a single forensic artifact left behind after an attack
B) TTPs and IOCs are interchangeable terms both referring to the same category of threat intelligence data
C) A TTP is only relevant to vulnerability management activities, while an IOC is only relevant to incident response activities
D) A TTP describes the behavior and methodology used by a threat actor, while an IOC is a specific artifact such as a file hash, IP address, or domain indicating compromise

---

**Q11.** A SOAR platform's playbook triggers when an EDR tool raises a 'malware detected' alert. The playbook automatically isolates the affected host from the network without any analyst intervention, then creates a ticket for later human review. Which type of SOAR capability does the automatic host-isolation step BEST represent?

A) Orchestration
B) Enrichment
C) Case management
D) Automation

---

**Q12.** An analyst notices repeated DNS queries from an internal workstation to a newly registered domain (NRD) with a very low reputation score, resolving to an IP address unrelated to any known business partner. Which action should the analyst take FIRST to contain potential C2 activity while preserving evidence for further investigation?

A) Immediately reimage the workstation to remove any malware present
B) Add the malicious domain to a DNS sinkhole/blackhole list to redirect and monitor further requests
C) Block all outbound DNS traffic from the network to prevent further domain resolution
D) Send an email to the user asking about recent activity on the workstation

---

**Q13.** A company's SOC notices a workstation generating DNS queries every 60 seconds to random 20-character subdomains of a rarely-used TLD, each resolving to a different low-TTL IP address. Which technique BEST helps confirm this is malicious C2 beaconing rather than legitimate CDN traffic?

A) Analyze the DNS query timing intervals and subdomain entropy using DNS logs, then check the domains against threat intelligence and passive DNS reputation feeds
B) Perform a full packet capture of all outbound HTTP traffic for the past 30 days
C) Disable DNS resolution for the workstation and monitor for user complaints
D) Add the workstation to a VLAN with no internet access and reimage it immediately

---

**Q14.** An analyst mapping a recent intrusion to the MITRE ATT&CK framework observes the attacker running "reg save hklm\sam sam.hive" and then using Mimikatz to extract plaintext credentials from LSASS memory. Which ATT&CK tactic does this activity fall under?

A) Privilege Escalation
B) Credential Access
C) Discovery
D) Lateral Movement

---

**Q15.** A SOC wants to reduce mean time to respond (MTTR) for critical malware alerts. They configure a SOAR playbook that triggers automatically when the SIEM generates a 'Critical' severity alert with a matched malicious file hash. Which playbook action BEST demonstrates effective security orchestration to contain the threat without waiting for analyst intervention?

A) Send an email notification to the SOC team distribution list for manual review
B) Log the alert to a ticketing system and wait for analyst triage during business hours
C) Call the EDR platform's API to automatically isolate the affected host from the network and open an incident ticket
D) Increase the SIEM alert threshold to reduce the number of similar future alerts

---

**Q16.** A security analyst wants to reduce false positives and gain accurate visibility into missing patches and misconfigurations on internal Windows servers, but is concerned about scan performance impact during business hours. Which approach BEST meets these requirements?

A) Non-credentialed active scan run continuously
B) Passive network scan using a network tap
C) Credentialed scan scheduled during a maintenance window
D) Agentless scan using SNMP only

---

**Q17.** An organization has a large remote workforce with laptops that connect intermittently to the corporate VPN, sometimes only once every few weeks. The security team needs continuous vulnerability visibility on these devices regardless of network connectivity. Which scanning approach BEST satisfies this requirement?

A) Network-based agentless scanning from an internal scanner
B) Passive scanning via a network TAP at the VPN concentrator
C) Agent-based scanning with a local scan engine and periodic result upload
D) Non-credentialed external scan of the corporate IP range

---

**Q18.** A vulnerability report lists a finding with the CVSS v3.1 vector: AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H. Based on this vector, which statement is accurate?

A) The vulnerability requires user interaction and physical access to exploit
B) The vulnerability can be exploited remotely over the network without authentication or user interaction, with high impact to confidentiality, integrity, and availability
C) The vulnerability only affects availability and requires local access
D) The vulnerability requires high privileges and only impacts confidentiality

---

**Q19.** A vulnerability scan identifies two findings on internet-facing servers. Finding 1: CVSS base score 9.8, no known public exploit, affects a rarely used internal reporting tool. Finding 2: CVSS base score 7.5, active exploit code is publicly available and being used in the wild, affects the organization's customer-facing payment gateway. Which finding should the analyst prioritize for remediation FIRST?

A) Finding 1, because its CVSS score is highest
B) Both findings equally, since CVSS scores should always drive prioritization order
C) Neither, until a formal risk acceptance is documented
D) Finding 2, because of active exploitation and high asset criticality despite a lower CVSS score

---

**Q20.** Which control is MOST effective at mitigating a broken access control vulnerability where users can access other users' records by modifying an object ID in a URL parameter?

A) Implementing server-side authorization checks that verify the requesting user owns or is permitted access to the requested object
B) Enforcing strong password complexity requirements
C) Enabling TLS 1.3 encryption for all API traffic
D) Rate limiting API requests to prevent brute-force attacks

---

**Q21.** A vulnerability scan identifies a critical remote code execution vulnerability (CVSS 9.8) on a legacy manufacturing control system. The vendor patch is not yet available, and the organization's patching SLA requires critical vulnerabilities be remediated within 15 days. The system cannot be taken offline without halting production. Which action should the analyst recommend to address the SLA requirement while the patch is unavailable?

A) Ignore the SLA since no patch exists
B) Immediately decommission the manufacturing system
C) Implement compensating controls such as network segmentation and enhanced monitoring, and document risk acceptance until a patch is released
D) Wait until the vendor releases a patch with no interim action

---

**Q22.** A company runs workloads in ephemeral Kubernetes containers that spin up and terminate within minutes. Security needs continuous vulnerability visibility across every container image running in the cluster without impacting container startup time or image build pipelines. Which scanning approach BEST meets this requirement?

A) Credentialed network scan against the cluster's internal IP range on a nightly schedule
B) Agent-based scanning with a dedicated vulnerability agent installed inside every container image
C) Non-credentialed external scan against the cluster's public-facing load balancer
D) Agentless scanning integrated via the cloud/container platform API to inspect image layers and running workloads

---

**Q23.** A SCADA environment controlling industrial equipment cannot tolerate any additional network traffic being sent to field devices, as this has previously caused equipment instability. The analyst still needs to identify vulnerable services running on these devices. Which scanning method should be used?

A) Active credentialed scan using vendor-supplied administrative credentials
B) Agent-based scanning with an agent installed on each PLC controller
C) Non-credentialed active scan using default service detection probes
D) Passive vulnerability scanning using a network tap or SPAN port to analyze existing traffic

---

**Q24.** A vulnerability scan reports a finding with a CVSS v3.1 Base Score of 9.8 (Critical). After applying environmental metrics reflecting the organization's actual deployment — the affected service sits behind a WAF, is isolated on a segmented VLAN with no internet access, and requires local authentication — the Environmental Score is recalculated to 4.3. When prioritizing remediation on the internal risk register, which score should the analyst use to represent the organization's actual risk?

A) The unmodified Base Score of 9.8, since it reflects the worst-case severity of the vulnerability itself
B) The Environmental Score of 4.3, since it reflects the compensating controls and actual deployment context
C) The Temporal Score, since it accounts for exploit code maturity independent of environment
D) The vulnerability's CVE publish date, since older CVEs are inherently lower priority

---

**Q25.** A DevSecOps team wants to integrate a testing tool directly into the CI pipeline that analyzes application source code for injection flaws, hardcoded credentials, and insecure coding patterns before the application is compiled or deployed to any runtime environment. Which testing type should be integrated?

A) Dynamic Application Security Testing (DAST)
B) Static Application Security Testing (SAST)
C) Manual penetration testing against a staging environment
D) Interactive Application Security Testing (IAST) using runtime instrumentation

---

**Q26.** A hospital's legacy infusion pump control system runs an unsupported OS version and cannot be patched due to FDA medical device certification requirements. A critical CVE with a publicly available exploit affects this system. Which action represents the BEST compensating control while the organization pursues a long-term replacement?

A) Isolate the device on a dedicated segmented VLAN with strict ACLs and continuous IDS monitoring
B) Replace the device in production immediately without vendor coordination
C) Formally document risk acceptance and take no further action until replacement
D) Manually uninstall the vulnerable service on the device without vendor approval

---

**Q27.** According to standard vulnerability management frameworks, which factor primarily determines the recommended remediation SLA (e.g., 24 hours, 7 days, 30 days) assigned to a given vulnerability finding?

A) The CVSS severity rating combined with real-world exploit availability
B) The number of days the vulnerability has appeared on prior scan reports
C) The total count of open tickets currently assigned to the security team
D) The vendor's published patch release schedule regardless of severity

---

**Q28.** A security team manages 5,000 laptops that frequently connect from home networks outside the corporate VPN, making them unreachable by the network-based scanner during business hours. Which vulnerability scanning approach BEST ensures consistent coverage of these endpoints?

A) Increase the frequency of non-credentialed network scans from the on-premises scanner
B) Deploy an agent-based scanning solution that reports findings whenever the device has internet connectivity
C) Switch to passive network monitoring using a SPAN port on the corporate switch
D) Schedule credentialed scans to run only during off-hours when devices are on the corporate network

---

**Q29.** A vulnerability scan flags a critical CVE affecting a legacy SCADA controller on the plant floor. The vendor has confirmed no patch will ever be released for this end-of-life device, and replacing it requires a planned outage six months away. Which action is the MOST appropriate immediate response?

A) Accept the risk and take no further action until the replacement is installed
B) Formally document risk acceptance and take no other action
C) Isolate the device on a segmented VLAN with strict firewall rules as a compensating control while tracking it for the planned replacement
D) Force the device offline immediately to eliminate the exposure

---

**Q30.** During a post-incident review, analysts want to map an adversary's observed techniques to a single, granular reference of tactics and procedures to identify detection gaps in their SIEM rules. Which framework should they use for this specific purpose?

A) MITRE ATT&CK matrix
B) Cyber Kill Chain
C) Diamond Model of Intrusion Analysis
D) OWASP Top 10

---

**Q31.** An incident responder documents the adversary, the capability used, the infrastructure involved, and the victim for a single confirmed intrusion event. Which analytic model is being applied?

A) Diamond Model of Intrusion Analysis
B) Lockheed Martin Cyber Kill Chain
C) MITRE ATT&CK
D) NIST incident response lifecycle

---

**Q32.** A ransomware infection is spreading rapidly across a hospital's clinical network. Patient care systems on the same VLAN are not yet infected but are at imminent risk. Analysts cannot immediately identify patient zero. Which containment action is MOST appropriate?

A) Isolate the affected VLAN segment at the switch/firewall level to stop lateral spread while preserving system state
B) Power off all domain controllers enterprise-wide to stop authentication-based lateral movement
C) Wait until eradication tools are ready before taking any containment action to avoid disrupting operations
D) Immediately wipe and reimage every endpoint on the affected VLAN

---

**Q33.** A forensic analyst removes a hard drive from a compromised server to be used as evidence in a future legal proceeding. Which action is REQUIRED immediately upon taking possession of the drive to maintain its evidentiary value?

A) Copy files from the drive directly to a shared network folder for the team to review
B) Install analysis tools directly onto the original drive to begin investigation immediately
C) Store the drive in the analyst's personal desk drawer until the investigation concludes
D) Begin documenting the chain of custody, including who handled the evidence, when, and why

---

**Q34.** Following eradication and recovery from a data breach, the incident response team holds a meeting to determine why existing controls failed to detect the intrusion for three months and to identify permanent process improvements. Which post-incident activity does this represent?

A) Tabletop exercise
B) Business impact analysis
C) Root cause analysis and lessons learned review
D) Chain of custody verification

---

**Q35.** An organization's incident response plan assigns a specific individual to be the single point of contact for all external media inquiries and regulatory notifications during an active incident. Which IR plan component defines this responsibility?

A) The communication plan
B) The evidence retention policy
C) The vulnerability scanning schedule
D) The business continuity plan

---

**Q36.** A financial services company detects ransomware actively encrypting files on a critical file server. The incident response team must stop the encryption from spreading to other systems while preserving volatile memory evidence for later forensic analysis. Which containment action BEST meets these requirements?

A) Power off the server immediately to halt the encryption process
B) Restore the server from the most recent backup immediately
C) Continue monitoring the server without taking any containment action
D) Isolate the server from the network (e.g., disable its network interface) while keeping it powered on

---

**Q37.** An analyst wants to document the specific tactics, techniques, and sub-techniques an adversary used during an intrusion, and map them to known detection and mitigation strategies for future reference. Which framework should the analyst use?

A) Cyber Kill Chain
B) MITRE ATT&CK
C) Diamond Model of Intrusion Analysis
D) OWASP Top 10

---

**Q38.** During incident response, an analyst is collecting evidence from a compromised Linux server following the order of volatility. Which of the following should be collected FIRST?

A) Data stored on the hard disk
B) Archived log files on backup tapes
C) Network configuration files stored on disk
D) CPU cache and registers

---

**Q39.** A vulnerability scan identifies a critical unpatched vulnerability on a legacy manufacturing control system. The system owner states that patching would require a six-month maintenance window and could void the vendor's support contract. Which of the following BEST describes this situation in a vulnerability management report?

A) A risk that should be accepted without documentation
B) An inhibitor to remediation that requires compensating controls
C) A false positive that should be excluded from the report
D) A vulnerability that should be immediately exploited to test compensating controls

---

**Q40.** During an incident response investigation, an analyst confirms that an attacker exfiltrated a database containing customer Social Security numbers. In addition to the incident response team and IT management, which stakeholder MUST be notified immediately based on this finding?

A) The help desk supervisor
B) The database vendor's sales representative
C) Legal counsel and compliance/privacy officer
D) The marketing department for a press release

---

**Q41.** An organization's incident response report shows the average time between an intrusion occurring and the security team identifying it. Which metric does this describe?

A) Mean time to remediate (MTTR)
B) Mean time to contain (MTTC)
C) Mean time to detect (MTTD)
D) Service level agreement (SLA) uptime

---

**Q42.** A CySA+ analyst needs to communicate vulnerability scan results to the executive leadership team, who have limited technical background but need to make budget decisions. Which type of report is MOST appropriate?

A) A detailed technical remediation runbook for each finding
B) A high-level executive summary with risk trends, business impact, and prioritized recommendations
C) A raw vulnerability scanner output with CVE details and CVSS vectors
D) A packet capture analysis of exploited vulnerabilities

---

**Q43.** After containing a ransomware incident, the incident response team wants to determine the underlying reason the initial phishing email bypassed email security controls. Which technique should the team use during the root cause analysis phase?

A) A vulnerability scan of all endpoints
B) A tabletop exercise for the next incident
C) A penetration test of the production network
D) The five whys technique

---

**Q44.** Two weeks after a major data breach has been fully remediated, the incident response manager schedules a meeting with all stakeholders involved in the response. Attendees will review what worked well, what didn't, and update the incident response plan. This meeting is BEST described as which of the following?

A) An incident declaration meeting
B) A tabletop exercise
C) A lessons learned/after-action review
D) A root cause analysis session

---

**Q45.** A vulnerability scan flags a critical CVE on a server that runs a proprietary manufacturing control application. The vendor of that application went out of business in 2019, the OS cannot be upgraded without breaking compatibility, and replacing the hardware would cost the company an estimated $2 million. The security analyst must document this in the vulnerability management report. Which inhibitor to remediation should be recorded?

A) Business process interruption
B) Memorandum of understanding (MOU)
C) Service level agreement (SLA) violation
D) Legacy systems

---

**Q46.** During a post-incident review meeting, the team finds that escalation to the CISO was delayed three hours because the on-call security analyst did not know who to contact after normal business hours. This finding, along with the proposed action item to create an updated after-hours escalation contact list, should be documented in which type of report?

A) Root cause analysis report
B) Compliance report
C) Lessons learned report
D) Vulnerability scan report

---

