## Chapter 12: Full Exam Simulation and Time-Management Strategy — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | CS0-003 exam format: total questions and time limit? | Up to 85 questions (MCQ + PBQ), 165 minutes. Exam tip: budget ~60-90 sec/MCQ, 8-10 min/PBQ. |
| 2 | CS0-003 passing score? | 750 on a scale of 100-900. Exam tip: not all questions are equally weighted — PBQs and heavily-tested domains matter more. |
| 3 | CVSS v3.1 severity ranges? | None: 0.0 \| Low: 0.1-3.9 \| Medium: 4.0-6.9 \| High: 7.0-8.9 \| Critical: 9.0-10.0. Exam tip: memorize exact cutoffs, not just labels. |
| 4 | False Positive vs False Negative | False Positive = alert on benign activity (wastes analyst time). False Negative = real threat goes undetected (worse outcome). Exam tip: tuning reduces false positives; missed detections are false negatives. |
| 5 | Containment vs Eradication vs Recovery | Containment = stop the spread (isolate). Eradication = remove the root cause (delete malware, patch). Recovery = restore systems to normal operation. Exam tip: sequence always Containment → Eradication → Recovery. |
| 6 | CVSS Base vs Environmental Score | Base = intrinsic severity, same for everyone. Environmental = adjusted for the organization's actual context (asset criticality, exposure). Exam tip: prioritization decisions should favor Environmental context over raw Base Score. |
| 7 | NIST IR phase order (SP 800-61) | Preparation → Detection & Analysis → Containment/Eradication/Recovery → Post-Incident Activity. Exam tip: this exact sequence is tested via scenario ordering questions. |
| 8 | CS0-003 domain review priority when time-limited | Review Security Operations (~33%) and Vulnerability Management (~30%) flagged items first — they carry ~63% combined weight vs Incident Response (~20%) and Reporting (~17%). |
| 9 | Cross-domain trap: CVSS score vs business context | A high CVSS score on an isolated, low-value asset ranks below a moderate CVSS score on an internet-facing critical asset. Exam tip: always apply asset context before ranking. |
| 10 | PBQ triage workflow during the exam | 1) Skim all MCQs first and answer confidently-known ones. 2) Flag uncertain MCQs. 3) Attempt PBQs only after securing MCQ credit. 4) Return to flagged items with remaining time. |
| 11 | PBQ vs MCQ time allocation ratio | PBQs typically consume 5-8x more time than a single MCQ (8-10 min vs 60-90 sec). Exam tip: never let one PBQ consume time needed for multiple MCQs. |
| 12 | Final readiness self-check before scheduling the exam | Score 85%+ consistently on domain-weighted practice exams AND be able to explain (not just recall) containment vs eradication, CVSS scoring, and log-based false positive/negative triage without hesitation. |
