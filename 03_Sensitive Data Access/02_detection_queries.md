## Detection – Sensitive Data Access

### Detection Goal
Identify post-compromise access to sensitive corporate data using both SIEM (Splunk) and host-based audit logs (auditd).

---

## 1. Splunk Detection (SIEM)

### Primary Detection Query
```spl
index=main sourcetype=linux_audit "CONFIDENTIAL_CEO_STRATEGY_Q4"
index=main sourcetype=linux_audit type=EXECVE
| search a0=cat OR a0=ls
| table _time host a0 a1 uid auid

2. Host-Based Investigation (auditd)
auditd Rule Triggered
-w /home/martin_kedob/CompanySecrets -p rwa -k sensitive_access


This rule was designed to monitor:

Read

Write

Attribute changes
on sensitive corporate data.

auditd Investigation Command
sudo ausearch -k sensitive_access -i
or just simply ausearch -k cmd_exec | grep "CONFIDENTIAL_CEO_STRATEGY_Q4" and investigate post brute force access time
