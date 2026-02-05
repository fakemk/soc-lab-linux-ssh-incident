# Detection – User Creation and Privilege Persistence

This stage was identified using both Splunk and auditd logs to confirm account creation, privilege assignment, and system-level configuration changes.

---

## Splunk – User Creation Activity

### Query

index=main sourcetype=linux_audit useradd
Explanation

This query searches audit logs for executions of the useradd binary.
Multiple events confirmed the creation of a new local user shortly after sensitive data access.

These events indicate deliberate persistence rather than normal administrative activity.

## Auditd – Command Execution Confirmation
Command : 
sudo ausearch -k cmd_exec -i | grep "useradd"

- Explanation

This command extracts audit events tagged with cmd_exec related to useradd.
The output confirms:

The exact command executed

The UID and EUID used (root)

The shell and execution context

## Auditd – Privilege Modification Evidence
Command
sudo ausearch -k cmd_exec -i | grep "usermod"

- Explanation

This confirms the execution of usermod to add the persistence account to the sudo group.
The presence of repeated execution attempts suggests intentional configuration rather than error.

## Auditd – Account Configuration File Access
Command
sudo ausearch -k cmd_exec -i | grep "/var/lib/AccountsService"

Explanation

This shows access to system account configuration files under:

/var/lib/AccountsService/users/

While not strictly required for privilege escalation, this step suggests the attacker verified or adjusted user metadata to ensure the account appears legitimate to the system and desktop services.
