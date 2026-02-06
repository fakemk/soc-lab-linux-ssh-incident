SOC Lab – Linux SSH Incident Investigation
Overview

TThis lab documents a SOC Level 1 investigation of a Linux SSH compromise involving brute-force authentication, privilege escalation, and persistence, using Splunk and auditd logs.
Scenario

An attacker performed multiple failed SSH authentication attempts against a Linux host. After successfully authenticating using valid credentials, the attacker escalated privileges via sudo, created a persistent local account, and accessed sensitive files on the system.
Environment

    Ubuntu Linux (victim VM)
    Kali Linux (attacker VM)
    Splunk Enterprise
    auditd
    Splunk Enterprise (SIEM)

Tools Used

    Splunk SIEM
    auditd
    Linux authentication logs
    SSH

Objectives

    Detect SSH brute-force activity
    Identify successful authentication
    Investigate sudo usage
    Detect account creation and persistence
    Confirm access to sensitive files
    Correlate auditd and Splunk logs

Outcome

Unauthorized access was confirmed, followed by privilege escalation, persistence via account creation, and access to sensitive files.
Disclaimer
This lab was conducted in a controlled environment for defensive security learning only.
