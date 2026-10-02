## Chapter 1 Cheat Sheet — System & Network Architecture Concepts

### Syslog Severity Levels
| Level | Name | Level | Name |
|---|---|---|---|
| 0 | Emergency | 4 | Warning |
| 1 | Alert | 5 | Notice |
| 2 | Critical | 6 | Informational |
| 3 | Error | 7 | Debug |
Lower number = more severe. Ports: UDP/TCP 514 (plaintext), TCP 6514 (TLS, RFC 5425).

### Log Forwarding Mechanisms
| Source | Mechanism | Port(s) |
|---|---|---|
| Linux/network devices | Syslog (rsyslog/syslog-ng) | 514 / 6514 (TLS) |
| Windows | WEF (WinRM/WS-Man) | 5985 (HTTP) / 5986 (HTTPS) |
| Cloud | API/agent push to SIEM (e.g., CloudTrail, Azure Monitor) | HTTPS 443 |

### Identity & Access Models
| Model | Definition | Exam Tip |
|---|---|---|
| RBAC | Access tied to role/group | Simplest, static |
| ABAC | Access tied to attributes (time, location, device) | Granular, dynamic, fits Zero Trust |
| PAM | Manages/monitors privileged accounts | Enables JIT elevation + session recording |
| Federation | Trust between identity domains (SAML/OAuth/OIDC) | SSO across orgs |
| Zero Trust | Never trust, always verify (NIST SP 800-207) | Micro-segmentation + continuous auth |

### MFA Factor Categories
- Something you **know** (password/PIN)
- Something you **have** (token, smartcard)
- Something you **are** (biometric)
True MFA = factors from ≥2 different categories.

### Encryption Fundamentals
| Type | Examples | Use Case |
|---|---|---|
| Symmetric | AES-128/256 | Fast, bulk data encryption |
| Asymmetric | RSA-2048/4096, ECC-256/521 | Key exchange, digital signatures |
| Hybrid | AES + RSA | TLS, PGP — asymmetric protects the symmetric key |

TLS 1.3: 1-RTT handshake (0-RTT resumption), drops weak ciphers. TLS 1.0/1.1: deprecated per RFC 8996 — never the right answer.

### PKI Components
| Component | Role |
|---|---|
| CA | Issues/signs certificates |
| RA | Verifies identity before issuance |
| CRL | Full list of revoked certs (offline check) |
| OCSP | Real-time single-cert revocation check |

### Sensitive Data Protection
| Technique | Description | Reversible? |
|---|---|---|
| Encryption | Ciphertext, key-based | Yes (with key) |
| Tokenization | Replaces data with vault-mapped token | No (without vault access) |
| Masking | Partial redaction for display | N/A (display-only) |
| DLP | Detects/blocks sensitive data in motion/at rest/in use | N/A |

Data classification tiers (common): Public → Internal → Confidential → Restricted.
