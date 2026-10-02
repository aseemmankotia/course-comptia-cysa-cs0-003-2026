## Chapter 6: Vulnerability Management: Analyzing and Prioritizing Vulnerability Data — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | CVSS v3.1 severity rating ranges? | None: 0.0 \| Low: 0.1–3.9 \| Medium: 4.0–6.9 \| High: 7.0–8.9 \| Critical: 9.0–10.0. Exam tip: memorize exact boundaries — questions test edge cases like 6.9 vs 7.0. |
| 2 | What are the 8 CVSS v3.1 Base metrics? | AV (Attack Vector), AC (Attack Complexity), PR (Privileges Required), UI (User Interaction), S (Scope), C/I/A (Confidentiality/Integrity/Availability Impact). Exam tip: Base metrics never change over time. |
| 3 | CVSS Temporal metric group components? | E (Exploit Code Maturity), RL (Remediation Level), RC (Report Confidence). Exam tip: these change over time as exploit tools/patches emerge, unlike Base metrics. |
| 4 | CVSS Environmental metric group components? | Modified Base metrics + CR/IR/AR (Confidentiality/Integrity/Availability Requirements). Exam tip: this is the only group that lets analysts factor in organization-specific asset value and compensating controls. |
| 5 | CVE ID format? | CVE-YYYY-NNNN (year + at least 4-digit sequence number, e.g., CVE-2024-12345). Exam tip: CVE identifies a vulnerability; CVSS scores its severity — not the same thing. |
| 6 | Zero-day vulnerability definition and exam-correct first response | A vulnerability actively exploited or disclosed before a vendor patch/CVE exists. Exam tip: correct first response is compensating controls (IPS/WAF signatures, segmentation, disabling the feature) — NOT waiting for a CVE or patch. |
| 7 | Base score vs Environmental score — which reflects org-specific risk? | Environmental score. Base is a static, worst-case theoretical value; Environmental applies Modified Base metrics + CR/IR/AR to reflect real deployment and asset criticality. |
| 8 | CVSS vector AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H — score & rating? | 9.8, Critical. Exam tip: this is the classic 'worst case, network exploitable, no auth, full CIA impact' vector you should recognize instantly. |
| 9 | Attack Vector (AV) metric values, most to least severe | Network (N) > Adjacent (A) > Local (L) > Physical (P). Exam tip: Network = remotely exploitable over the internet = highest severity contribution. |
| 10 | Exploitability indicators that raise prioritization beyond raw CVSS score | Public exploit code (PoC/weaponized), active exploitation in the wild, internet-facing exposure, low attack complexity. Exam tip: these context factors can push a Medium-scored vuln to top priority. |
| 11 | Internet-facing vs internal asset — exam prioritization rule | All else equal, internet-facing systems get remediation priority over internal-only systems due to greater attack surface. Exam tip: exposure is a context factor, separate from the CVSS Base score itself. |
| 12 | Compensating control example and where to reflect it in CVSS | A WAF blocking a specific SQLi pattern is a compensating control. Exam tip: reflect this via Environmental metrics (Modified Base metrics), NOT by changing the immutable Base score. |
