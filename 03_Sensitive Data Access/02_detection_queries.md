## Detection – Sensitive Data Access

### Detection Goal
Identify post-compromise access to sensitive corporate data using both SIEM (Splunk) and host-based audit logs (auditd).

---

## 1. Splunk Detection (SIEM)

### Primary Detection Query

index=main sourcetype=linux_audit "CONFIDENTIAL_CEO_STRATEGY_Q4"

# Supporting Query

index=main sourcetype=linux_audit type=EXECVE

| search a0=cat OR a0=ls

| table _time host a0 a1 uid auid

----
# What this shows

Execution of file access commands (cat, ls) against sensitive files

Direct reference to the file CONFIDENTIAL_CEO_STRATEGY_Q4

User context (uid, auid) responsible for the access

Timestamp and host where the activity occurred

---


## 2. Host-Based Investigation (auditd)

auditd Rule Triggered

-w /home/martin_kedob/CompanySecrets -p rwa -k sensitive_access

---

# This rule monitors:

Read operations on sensitive files

Write operations to sensitive directories

Attribute or permission changes

All activity within the CompanySecrets directory

---

# auditd Investigation Commands
sudo ausearch -k sensitive_access -i
or
sudo ausearch -k cmd_exec -i | grep "CONFIDENTIAL_CEO_STRATEGY_Q4"

#What this confirms

Direct interaction with sensitive files after successful SSH authentication

Commands executed from the compromised user session

Clear temporal linkage between credential compromise and data access

Host-level confirmation of activity observed in Splunk

-----

# Why this matters

Confirms execution of post-compromise objectives (data access)

Demonstrates attacker intent beyond initial access

Validates SIEM findings using authoritative host-based evidence

Establishes a high-impact breach involving sensitive corporate data
