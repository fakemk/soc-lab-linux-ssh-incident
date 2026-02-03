Stage 3 – Sensitive Data Access

What happened
The attacker accessed and listed sensitive corporate files located in the CompanySecrets directory.

Why this matters
Access to sensitive local files may lead to data leakage or further abuse.

MITRE ATT&CK
• T1005 – Data from Local System

Evidence
Auditd logs + splunk logs show file access and command execution against sensitive files.
