# Stage 3 – Sensitive Data Access

## What happened
The attacker accessed and interacted with sensitive corporate files located in the `CompanySecrets` directory.

## Why this matters
Unauthorized access to sensitive local files can result in data leakage, extortion, or further compromise.

## MITRE ATT&CK
- T1005 – Data from Local System

## Evidence
Auditd and Splunk logs confirm command execution and file access to sensitive data.
