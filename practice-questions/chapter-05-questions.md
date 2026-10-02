## Chapter 5: Vulnerability Management: Scanning Methods and Concepts — Practice Questions

**Q1.** A security team must assess vulnerabilities on a production SCADA system that controls physical manufacturing equipment. The vendor states the device firmware crashes under network probing. Which scanning approach BEST meets this requirement?

A) Run a credentialed active scan during business hours to maximize accuracy
B) Install a scanning agent directly on the SCADA controller
C) Deploy passive scanning to monitor network traffic and identify vulnerabilities without sending packets to the device
D) Run a non-credentialed scan with aggressive timing templates

<details>
<summary>Answer</summary>

**Correct: C**

Passive scanning analyzes existing network traffic (protocol banners, version strings) without sending any packets to the fragile device, eliminating the crash risk while still surfacing vulnerability indicators.

**Why the others are wrong:**
- Any active scan, credentialed or not, sends probe traffic that can crash fragile ICS/SCADA firmware — accuracy doesn't offset the operational risk.
- Most legacy ICS controllers cannot run modern OS agents (no compute headroom, unsupported OS, vendor prohibits third-party software).
- Aggressive timing templates increase packet volume and connection load, which is exactly what causes fragile-system crashes.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An analyst has valid administrative credentials for all Windows servers in scope and wants to minimize false positives when checking for missing patches. Which scan type should be configured?

A) Non-credentialed external scan
B) Passive network traffic scan
C) Credentialed scan using the provided administrative credentials
D) Agentless discovery scan with no authentication

<details>
<summary>Answer</summary>

**Correct: C**

Credentialed scans log into the host (via SMB/WinRM) to directly query installed patches, registry keys, and software versions, dramatically reducing false positives/negatives compared to remote fingerprinting.

**Why the others are wrong:**
- Non-credentialed scans infer patch state from banners and responses, producing higher false positive/negative rates.
- Passive scanning only observes traffic already on the wire and cannot query local patch-level details.
- Discovery-only scans (no authentication) identify that a host exists but do not enumerate patch/vulnerability data.

</details>

---

**Q3.** A network is divided into isolated VLANs separated by firewalls with default-deny rules. Management wants full vulnerability visibility into every segment without creating new firewall exceptions. What is the BEST solution?

A) Configure a single central scanner and open firewall rules to route scan traffic to every VLAN
B) Perform passive traffic capture only at the network perimeter
C) Run a non-credentialed scan from the DMZ toward each internal segment
D) Deploy a local scan engine or agent within each segmented VLAN and aggregate results centrally

<details>
<summary>Answer</summary>

**Correct: D**

Placing a distributed scan engine or agents inside each segment avoids punching new holes in the segmentation boundary while still giving each zone a fully authenticated, in-segment view of its assets.

**Why the others are wrong:**
- Opening firewall rules for a central scanner defeats the purpose of segmentation and increases attack surface — a common exam trap.
- Perimeter-only passive capture cannot see intra-VLAN traffic, so internal hosts within a segment remain unassessed.
- Scanning across segment boundaries from the DMZ is blocked by default-deny rules and would require the same rule exceptions being avoided.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A cloud team runs auto-scaling container workloads that frequently start and terminate within minutes, often before the nightly network vulnerability scan window. Which scanning method should be adopted?

A) A nightly non-credentialed network scan run at a fixed time
B) Passive scanning at a network tap outside the cloud VPC
C) A manual scan triggered by a helpdesk ticket after deployment
D) Agent-based scanning embedded in the container/VM image so data is collected at boot regardless of scan schedule

<details>
<summary>Answer</summary>

**Correct: D**

Baking a lightweight agent into the golden image ensures vulnerability data is captured the moment the ephemeral instance launches, independent of a scheduled scan window that short-lived assets may not survive.

**Why the others are wrong:**
- A fixed nightly network scan will miss instances that spin up and terminate between scan cycles — a classic ephemeral-asset gap.
- External passive capture on a tap typically can't see intra-VPC container traffic and adds no coverage for terminated instances.
- Manual, ticket-driven scanning does not scale to auto-scaling workloads and introduces unacceptable delay.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Which asset discovery technique identifies live hosts and services by observing existing network traffic without sending any packets to the targets?

A) Active scanning using a ping sweep
B) Credentialed scanning
C) Agent-based inventory polling
D) Passive scanning via traffic monitoring (e.g., packet capture or NetFlow analysis)

<details>
<summary>Answer</summary>

**Correct: D**

Passive discovery listens to traffic already traversing the network (via SPAN port, TAP, or flow data) to build an asset inventory with zero packets sent to the hosts themselves.

**Why the others are wrong:**
- A ping sweep is active by definition — it sends ICMP/ARP packets to elicit responses.
- Credentialed scanning requires actively connecting to and authenticating against the host.
- Agent-based inventory requires software running on the host that actively reports data, not passive observation.

</details>

---

**Q6.** A daily credentialed vulnerability scan of 10,000 hosts is causing noticeable network congestion and CPU spikes on production servers. Which configuration change BEST addresses this while preserving scan coverage?

A) Increase scan frequency to hourly for faster detection
B) Enable scan throttling and stagger scans across defined maintenance windows in smaller batches
C) Switch entirely to unauthenticated, external-only scans
D) Disable authentication so scans run faster

<details>
<summary>Answer</summary>

**Correct: B**

Throttling scan speed/thread count and staggering the 10,000 hosts across scheduled maintenance windows spreads load over time, reducing peak network and host impact without sacrificing credentialed accuracy.

**Why the others are wrong:**
- Increasing frequency to hourly would multiply, not reduce, the performance impact.
- Dropping to external-only unauthenticated scanning sacrifices accuracy and does not directly address the resource-consumption complaint (scan volume still occurs).
- Removing authentication reduces scan depth and accuracy for no meaningful performance gain, since network probing is still the bottleneck, not the login step.

</details>

---

**Q7.** A legacy networked medical infusion pump is known to lock up when scanned with standard vulnerability tools. Compliance still requires vulnerability tracking for this device. What is the appropriate scan configuration?

A) Exclude the device from active scanning, rely on passive traffic monitoring and vendor documentation, and note the exception with compensating controls
B) Full aggressive credentialed scan scheduled during peak patient-care hours
C) Non-credentialed scan with maximum parallel threads to finish quickly
D) Install a generic scanning agent on the device's embedded OS

<details>
<summary>Answer</summary>

**Correct: A**

For fragile/special systems, best practice is a scan exclusion with documented compensating controls (passive monitoring, vendor advisories, network segmentation) rather than risking patient safety with active probing.

**Why the others are wrong:**
- Aggressive active scanning is the exact behavior known to crash the device, and doing it during patient care compounds patient-safety risk.
- High thread count non-credentialed scanning still sends active probes, which is the root cause of the lockup regardless of credentials.
- Most embedded medical device OSes are proprietary/closed and don't support installing third-party agents, and vendors typically prohibit this.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What is the primary trade-off between agent-based and agentless vulnerability scanning?

A) Agentless scanning requires network reachability and open ports at scan time, while agent-based scanning reports continuously regardless of network location but requires software deployment and maintenance on every host
B) Agent-based scanning is always more accurate than any other method in every scenario
C) Agentless scanning cannot be used against any cloud-hosted assets
D) Agent-based scanning eliminates the need for any authentication or credentials

<details>
<summary>Answer</summary>

**Correct: A**

This is the core architectural trade-off tested on CS0-003: agentless depends on the target being online and network-accessible during the scan window, while agents provide always-on, location-independent visibility at the cost of deployment/patching overhead per endpoint.

**Why the others are wrong:**
- Accuracy depends on context — agentless credentialed scans can be equally accurate for always-on network assets; 'always more accurate' is an overgeneralization.
- Agentless scanning is routinely used against cloud assets via network scanning or cloud-provider APIs; the limitation is ephemeral timing, not impossibility.
- Agents still typically require some form of registration/authentication to a management console and don't inherently remove credential requirements for the data they collect.

</details>

---

