# Stage 4 – Privilege Escalation and Persistence

## What happened
The attacker abused sudo privileges to create a new local user with a deceptive name, modified group memberships, and edited account configuration files to maintain access.

## Why this matters
Account creation and privilege manipulation enable long-term persistence and bypass normal access controls.

## MITRE ATT&CK
- T1136.001 – Create Account (Local)
- T1098 – Account Manipulation
- T1548.003 – Abuse Elevation Control Mechanism: Sudo


## Evidence
Auditd and Splunk logs show sudo usage, user creation, group modification, and account configuration file edits.
