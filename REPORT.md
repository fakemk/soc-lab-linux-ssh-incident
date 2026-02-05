Incident Report – Linux SSH Compromise & Persistence
# 1. Executive Summary

On 2026-01-29, a Linux host (fairyCEO) was compromised via SSH brute-force, leading to successful authentication, privilege escalation, creation of a persistent account, and access to sensitive data.
The attacker originated from an internal IP and abused valid credentials to escalate privileges using sudo, then modified account configuration files to maintain persistence.


# 2. Timeline (UTC)
Initial Access – Brute Force

17:24:20

Multiple SSH failed login attempts

Target user: martin_kedob

Source IP: 192.168.7.109

Log source: /var/log/auth.log

Evidence: repeated Failed password for martin_kedob

Successful Authentication

17:24:17

Successful SSH login

User: martin_kedob

Source IP: 192.168.7.109

Port: 33898

Evidence: Accepted password for martin_kedob

Privilege Escalation

17:27:03 – 17:29:20

Multiple sudo sessions opened by martin_kedob

Effective user: root

Commands executed:

useradd

usermod

nano

Evidence:

pam_unix(sudo:session): session opened for user root

USER=root COMMAND=/usr/sbin/useradd

USER=root COMMAND=/usr/sbin/usermod

Persistence – Account Creation & Modification

17:27:14

New account creation:

Username: martinkedob

Home directory: /home/martinkedob

Shell: /bin/bash

Evidence:

exe=/usr/sbin/useradd

proctitle=/sbin/useradd -d /home/martinkedob

17:27:58

Account added to privileged groups:

sudo

Evidence:

usermod -aG sudo martinkedob

add 'martinkedob' to group 'sudo'
17:28:45

Direct modification of account service file:

/var/lib/AccountsService/users/martinkedob

Evidence:

nano /var/lib/AccountsService/users/martinkedob

Sensitive Data Access

17:25:25 – 17:25:50

Access to sensitive file:

CONFIDENTIAL_CEO_STRATEGY_Q4

Encrypted file: CONFIDENTIAL_CEO_STRATEGY_Q4.txt.gpg

Commands:

cat

ls

Directory:

/home/martin_kedob/CompanySecrets

Evidence:

type=EXECVE a0="cat" a1="CONFIDENTIAL_CEO_STRATEGY_Q4"

Audit key: sensitive_access

# 3. Indicators of Compromise (IOCs)
Network

Source IP:

192.168.7.109

_Accounts

Compromised user:

martin_kedob

Malicious / persistence account:

martinkedob

_Files

Sensitive data:

CONFIDENTIAL_CEO_STRATEGY_Q4

CONFIDENTIAL_CEO_STRATEGY_Q4.txt.gpg

Persistence file:

/var/lib/AccountsService/users/martinkedob

- Commands
ssh
sudo
useradd
usermod
nano
cat
ls

# 4. MITRE ATT&CK Mapping
Tactic	                 |Technique	              |  ID	     | Evidence
======================================================================================
Initial Access	         | Brute Force	          |T1110	   | Repeated failed SSH logins
Initial Access	         | Valid Accounts   	    |T1078     | Accepted SSH password
Privilege Escalation	   | Sudo	                  |T1548.003 | sudo root sessions
Persistence	             | Create Account	        |T1136.001 | useradd martinkedob
Persistence              |	Account Manipulation	|T1098	   | usermod -aG sudo
Defense Evasion	Modify   | System Files	          |T1565.001 | AccountsService file editing
Collection	             |  Data from Local System|	T1005	   | Access to confidential file

# 5. Lessons Learned

Password-based SSH authentication enabled brute-force success.

Excessive sudo privileges allowed full system compromise.

Account persistence was achieved without detection controls.

Sensitive data access was not blocked or alerted in real time.

# 6. Hardening & Recommendations
Authentication

Disable SSH password authentication.
Enforce SSH key-based login.

Implement account lockout after failed attempts.

Privilege Management

Apply least-privilege to sudoers.

Monitor sudo usage with real-time alerts.

Account Monitoring

Alert on:

useradd

usermod

Changes to /var/lib/AccountsService/

Daily audit of local accounts and groups.

Data Protection

Restrict access to sensitive directories.

Add audit rules for confidential file access.

Enable alerting on cat / ls of sensitive files.
