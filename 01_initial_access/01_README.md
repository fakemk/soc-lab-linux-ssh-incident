## Stage 1 – Initial Access (SSH Brute Force)

### What happened
Multiple failed SSH authentication attempts were observed against the CEO account
(martin_kedob) from a single internal IP address.

This indicates a password-guessing or brute-force attempt prior to successful access.

### Why this matters
Repeated authentication failures are a common precursor to account compromise
and must be investigated immediately by SOC analysts.
### MITRE ATT&CK
- T1110 – Brute Force
- T1078 – Valid Accounts (attempted)
