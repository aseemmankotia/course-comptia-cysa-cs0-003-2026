## Chapter 1: Security Operations: System and Network Architecture Concepts — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Syslog severity levels 0-7, in order? | 0=Emergency, 1=Alert, 2=Critical, 3=Error, 4=Warning, 5=Notice, 6=Informational, 7=Debug. Exam tip: lower number = higher severity. |
| 2 | Default syslog port (unencrypted) vs syslog-over-TLS port? | UDP/TCP 514 = unencrypted syslog. TCP 6514 = syslog over TLS (RFC 5425). Exam tip: choose 6514 when the scenario requires encrypted centralized log transport. |
| 3 | Windows Event Forwarding (WEF) transport ports? | 5985 = WinRM over HTTP, 5986 = WinRM over HTTPS. Exam tip: WEF uses WS-Management, not syslog, so it's Windows-only. |
| 4 | RBAC vs ABAC — key difference? | RBAC grants access based on job role/group membership. ABAC evaluates dynamic attributes (time, location, device posture). Exam tip: ABAC is more granular and fits Zero Trust models. |
| 5 | Zero Trust core principle (NIST SP 800-207)? | Never trust, always verify — authenticate and authorize every request regardless of network location. Exam tip: implemented via micro-segmentation + continuous verification, not perimeter defense. |
| 6 | What does PAM Just-In-Time (JIT) access do? | Grants elevated privileges only for a limited time window, then auto-revokes them. Exam tip: reduces risk of standing/permanent admin accounts being compromised. |
| 7 | TLS 1.3 vs TLS 1.2 — key improvements? | TLS 1.3 uses a 1-RTT handshake (0-RTT on session resumption) and drops weak ciphers (RC4, MD5, SHA-1, static RSA key exchange). Exam tip: TLS 1.0/1.1 are deprecated (RFC 8996) and are always wrong answers. |
| 8 | Symmetric vs asymmetric encryption — when to use each? | Symmetric (AES) = fast, single shared key, used for bulk data. Asymmetric (RSA/ECC) = slower, used for key exchange and digital signatures. Exam tip: hybrid encryption uses asymmetric keys to protect the symmetric key. |
| 9 | Relative key-strength: AES-256 vs RSA vs ECC? | NIST guidance: ECC-256 ≈ RSA-3072 in security strength; ECC-521 ≈ AES-256 equivalent. Exam tip: ECC gives equivalent security with much smaller keys — ideal for constrained devices. |
| 10 | OCSP vs CRL for revocation checking? | OCSP = real-time query for a single certificate's status. CRL = full downloadable list of revoked certs, checked offline. Exam tip: OCSP stapling reduces repeated client-to-CA lookups and improves performance. |
| 11 | MFA — the three factor categories? | Something you know (password), something you have (token/smartcard), something you are (biometric). Exam tip: true MFA requires factors from TWO DIFFERENT categories, not two passwords. |
| 12 | Tokenization vs masking vs encryption for sensitive data? | Tokenization = replaces data with a non-reversible token mapped in a secure vault. Masking = obscures data for display (e.g., last 4 digits shown). Encryption = reversible with a key. Exam tip: tokenization is preferred for PCI-DSS PAN protection since the real data never leaves the vault. |
