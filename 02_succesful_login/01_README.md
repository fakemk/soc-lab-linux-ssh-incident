####Stage 2 – Successful SSH Authentication

What happened
After multiple failed SSH attempts, the attacker successfully authenticated using valid credentials for the user martin_kedob.

Why this matters
A successful login following repeated failures confirms credential compromise and initial access.

MITRE ATT&CK
• T1078 – Valid Accounts
• T1021.004 – Remote Services (SSH)

Evidence
Splunk authentication logs show an accepted SSH login.

