## Chapter 4: Security Operations: Automation, Orchestration, and SOAR for Efficiency — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | SOAR stands for? | Security Orchestration, Automation, and Response. Exam tip: three words = three functions the platform performs (orchestrate tools, automate tasks, manage response/cases). |
| 2 | Automation vs Orchestration — core difference? | Automation = single repetitive task, one system, no human input. Orchestration = coordinating multiple tools/tasks into one workflow. Exam trap: questions swap these terms as distractors. |
| 3 | MTTD stands for and measures what? | Mean Time to Detect — elapsed time from compromise occurrence to SOC detection. SOAR reduces this via automated correlation and enrichment. |
| 4 | MTTR stands for and measures what? | Mean Time to Respond (or Repair) — elapsed time from detection to containment/remediation. SOAR reduces this via automated response playbooks. |
| 5 | What is 'dwell time' in incident response? | Time an attacker remains present/undetected in an environment, generally measured from initial compromise to full eradication. Related to but broader than MTTD. |
| 6 | Primary purpose of an enrichment playbook? | Automatically gather context (WHOIS, geolocation, reputation, sandbox results) on an alert before it reaches an analyst, reducing manual investigation time and alert fatigue. |
| 7 | What is 'human-in-the-loop' in SOAR design? | An approval checkpoint requiring analyst confirmation before a playbook executes a high-impact/destructive action (e.g., account disable, host isolation). Mitigates over-automation risk. |
| 8 | Risk of fully automating response actions with no review step? | Over-automation: a false positive can trigger a destructive action (blocking legitimate users, isolating production hosts) causing business disruption. Exam gotcha topic. |
| 9 | How does SOAR reduce analyst alert fatigue? | By auto-triaging and enriching low-fidelity alerts, suppressing/closing confirmed false positives, and escalating only alerts meeting defined criteria — reducing volume analysts must manually review. |
| 10 | Example of orchestration across tools (exam-style scenario)? | One trigger causes: firewall block update + EDR host isolation + SIEM case creation + ticket in ITSM — coordinated action across 4 disparate tools = orchestration, not automation. |
| 11 | Which metric does a SOAR playbook most directly improve first: MTTD or MTTR? | Both, but automated enrichment/correlation primarily lowers MTTD (faster detection), while automated response actions primarily lower MTTR (faster containment). Exam may ask which applies to which stage. |
| 12 | Playbook use case: repeated failed logins across multiple accounts from one source IP | Classic SOAR playbook trigger: auto-enrich source IP reputation, correlate across accounts, then (with or without approval gate) auto-block IP at firewall and open incident ticket. |
