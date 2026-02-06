# Stage 3 – Sensitive Data Access

## What happened
The attacker accessed sensitive corporate files located in the CompanySecrets directory, including the file CONFIDENTIAL_CEO_STRATEGY_Q4.

## Why this matters
Unauthorized access to sensitive local files can result in data leakage, extortion, or further compromise.

## MITRE ATT&CK
- T1005 – Data from Local System

## Evidence
Auditd and Splunk logs confirm command execution and access to sensitive files through commands such as cat and ls, including access to CONFIDENTIAL_CEO_STRATEGY_Q4.

