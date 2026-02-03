## Detection – Sensitive Data Access

### Detection Goal
Identify post-compromise access to sensitive corporate data using both SIEM (Splunk) and host-based audit logs (auditd).

---

## 1. Splunk Detection (SIEM)

### Primary Detection Query
```spl
index=main sourcetype=linux_audit "CONFIDENTIAL_CEO_STRATEGY_Q4"

Supporting Query
index=main sourcetype=linux_audit type=EXECVE
| search a0=cat OR a0=ls
| table _time host a0 a1 uid auid
What this shows

Execution of file access commands (cat, ls) against sensitive files

Filename CONFIDENTIAL_CEO_STRATEGY_Q4 referenced directly

User context (uid, auid) responsible for the access

Timestamp and host where the activity occurred

2. Host-Based Investigation (auditd)
auditd Rule Triggered
-w /home/martin_kedob/CompanySecrets -p rwa -k sensitive_access
auditd Investigation Commands
sudo ausearch -k sensitive_access -i
Alternative focused investigation: sudo ausearch -k cmd_exec -i | grep "CONFIDENTIAL_CEO_STRATEGY_Q4"
What this confirms

Direct interaction with sensitive files after successful SSH authentication

Commands executed from the compromised user session

Clear temporal linkage between credential compromise and data access

Host-level confirmation of activity observed in Splunk

Why this matters

Confirms post-compromise objective execution (data access)

Demonstrates attacker intent beyond initial access

Validates SIEM alerts using authoritative host-based evidence

Establishes high-impact breach involving sensitive corporate data
