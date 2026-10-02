## Chapter 1: Security Operations: System and Network Architecture Concepts — Practice Questions

**Q1.** A SOC analyst notices that Linux servers are sending logs via UDP port 514 to the SIEM, but critical authentication failure events are being dropped during high-traffic periods. Which change BEST resolves this?

A) Increase the UDP receive buffer size on the SIEM collector only
B) Switch to syslog over TCP or TLS on port 6514 for reliable, encrypted delivery
C) Force all servers to resynchronize with an NTP server
D) Migrate the Linux servers to Windows Event Forwarding

<details>
<summary>Answer</summary>

**Correct: B**

UDP syslog is connectionless with no delivery guarantee; switching to TCP (or TLS on 6514) provides acknowledged, reliable, and encrypted transport, preventing message loss under load.

**Why the others are wrong:**
- Buffer tuning may reduce drops slightly but doesn't fix the underlying lack of delivery guarantee in UDP.
- NTP sync affects timestamp accuracy, not packet loss.
- WEF is a Windows-specific mechanism using WinRM and doesn't apply to Linux syslog sources.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company adopts a Zero Trust architecture. An internal application server that previously trusted all traffic from the corporate LAN now requires explicit verification for every request. Which control implementation BEST reflects this shift?

A) A single perimeter firewall paired with a site-to-site VPN
B) Micro-segmentation with policy enforcement points that validate identity and context per session
C) A flat network using VLANs for department separation only
D) An allow-list based solely on source IP subnet

<details>
<summary>Answer</summary>

**Correct: B**

Zero Trust (NIST SP 800-207) requires continuous, per-session verification of identity and device posture at granular enforcement points rather than relying on network location.

**Why the others are wrong:**
- Perimeter firewall + VPN is classic castle-and-moat, the opposite of Zero Trust's 'never trust, always verify'.
- VLANs alone provide coarse segmentation but no identity-based verification of individual requests.
- Source-IP allow-listing assumes network location implies trust, which Zero Trust explicitly rejects.

</details>

---

**Q3.** During an audit, a security analyst discovers that a database administrator account has standing domain admin privileges used only twice a year for emergency patching. Which control BEST enforces least privilege here?

A) Delete the account entirely since it's rarely used
B) Force a password rotation every 30 days
C) Implement Privileged Access Management (PAM) with just-in-time elevation and session recording
D) Move the account into a separate Active Directory OU

<details>
<summary>Answer</summary>

**Correct: C**

PAM with JIT access grants domain admin rights only for the duration of the approved task and automatically revokes them afterward, eliminating standing privilege risk while preserving legitimate access when needed.

**Why the others are wrong:**
- Deleting the account removes needed emergency access capability entirely.
- Password rotation doesn't reduce the scope or duration of standing privileges.
- Moving the account to a different OU doesn't change its effective permissions.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** An organization must encrypt data in transit between microservices while minimizing handshake latency and eliminating support for deprecated cipher suites. Which protocol should be enforced?

A) SSL 3.0
B) TLS 1.0
C) TLS 1.3
D) TLS 1.2 with all legacy cipher suites enabled

<details>
<summary>Answer</summary>

**Correct: C**

TLS 1.3 removes support for weak/legacy ciphers (RC4, static RSA key exchange, SHA-1) and uses a 1-RTT handshake (0-RTT on resumption), reducing latency while improving security.

**Why the others are wrong:**
- SSL 3.0 is broken (POODLE) and disallowed on the exam and in practice.
- TLS 1.0/1.1 were formally deprecated by RFC 8996 and should never be selected as the answer.
- Enabling legacy ciphers on TLS 1.2 defeats the goal of eliminating deprecated cipher support.

</details>

---

**Q5.** A developer needs to encrypt a 5GB backup file quickly before uploading it to cloud storage, then securely share the decryption key with a partner organization. Which encryption approach BEST fits both requirements?

A) Encrypt the entire 5GB file directly using RSA-4096
B) Hash the file with SHA-256 before upload
C) Encrypt the file with AES-256, then encrypt the AES key with the partner's RSA public key (hybrid encryption)
D) Encrypt the entire file directly using ECC

<details>
<summary>Answer</summary>

**Correct: C**

Hybrid encryption uses fast symmetric AES-256 for bulk data and slower asymmetric RSA only to protect the small AES key, giving both speed and secure key exchange — this is how TLS and PGP work.

**Why the others are wrong:**
- Asymmetric algorithms like RSA are computationally expensive and impractical for encrypting large files directly.
- Hashing is one-way and provides integrity, not confidentiality — the file couldn't be recovered.
- Directly encrypting large data with ECC is not standard practice; ECC is used for key exchange/signatures, not bulk encryption.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A SIEM rule is configured to alert only on syslog messages with severity levels 0 through 2. Which type of events will this rule capture?

A) Debug and informational messages
B) Emergency, alert, and critical messages
C) Warning and notice messages
D) Error messages only

<details>
<summary>Answer</summary>

**Correct: B**

Syslog severity levels run 0 (Emergency) through 7 (Debug); levels 0-2 correspond to Emergency, Alert, and Critical — the highest-severity events.

**Why the others are wrong:**
- Debug (7) and Informational (6) are the lowest severities, the opposite end of the scale.
- Warning (4) and Notice (5) fall in the middle of the scale, not levels 0-2.
- Error is level 3, one step below Critical, and is excluded from a 0-2 filter.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A financial services company wants to prevent credit card numbers from being emailed outside the corporate network while still allowing analysts to reference the last four digits in reports. Which control BEST achieves this?

A) Full-disk encryption on all endpoints
B) VLAN segmentation between departments
C) Network-based DLP using pattern matching with tokenization/partial masking applied to PAN data
D) Multi-factor authentication on email accounts

<details>
<summary>Answer</summary>

**Correct: C**

Network DLP inspects outbound traffic for PAN patterns (regex) and can block or redact them, while tokenization/masking preserves usability (last four digits) without exposing the full number.

**Why the others are wrong:**
- Full-disk encryption protects data at rest on a stolen device, not data being emailed outbound.
- VLAN segmentation controls network reachability, not content leaving via email.
- MFA protects account access but does nothing to inspect or block outbound message content.

</details>

---

**Q8.** Which PKI component allows a client to check whether a certificate has been revoked in near real-time, without downloading a large revocation list?

A) Certificate Revocation List (CRL)
B) Registration Authority (RA)
C) Online Certificate Status Protocol (OCSP)
D) Root Certificate Authority (CA)

<details>
<summary>Answer</summary>

**Correct: C**

OCSP allows a client to query the status of a single certificate in real time from an OCSP responder, avoiding the overhead of downloading and parsing an entire CRL.

**Why the others are wrong:**
- A CRL is a full downloadable list of all revoked certificates, which is slower and less scalable than a single-certificate query.
- The RA verifies identity during certificate enrollment; it plays no role in revocation checking.
- The Root CA issues and signs certificates but is not queried directly for real-time revocation status.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

