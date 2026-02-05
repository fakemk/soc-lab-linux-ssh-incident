# SOC L1 Incident Report – SSH Compromise

## Alert Summary
Multiple failed SSH authentication attempts were followed by a successful login on a Linux host. Post-login activity indicates unauthorized access to sensitive files and account manipulation.

**Severity:** High  
**Confidence:** True Positive  
**Action:** Escalate to SOC L2

---

## Affected Asset
- Host: fairyCEO
- User: martin_kedob

---

## Key Findings
- Repeated SSH failed logins against a single account
- Successful SSH authentication from same source
- Access to sensitive local files (CompanySecrets)
- Sudo usage observed
- -high sensivity file was taken
- New local user created and modified
- Account configuration files edited

---

## Assessment
Confirmed credential compromise with privilege escalation and persistence activity.

---

## Gaps / Not Verified
- No network exfiltration analysis
- No persistence beyond local accounts confirmed
- No lateral movement investigation
-No obvious of malware (needs to be confirmed)
---

## Recommended Action
Escalate to SOC Level 2 for containment and full investigation.
