
tage 4 – Privilege Escalation and Persistence

What happened
The attacker used sudo privileges to create a new local user with a deceptive name, modified group membership, and edited account configuration files.

Why this matters
Unauthorized account creation and privilege assignment allows long-term persistent access.

MITRE ATT&CK
• T1136.001 – Create Account (Local)
• T1098 – Account Manipulation
• T1547 – Boot or Logon Autostart Execution

Evidence
Auditd and Splunk logs confirm user creation, group modification, and account configuration changes.
