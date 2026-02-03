Primary Detection Query
index=main sourcetype=linux_secure "Failed password"


What this shows

All failed authentication attempts recorded by sshd

Username targeted by the attacker

Source IP address

SSH port used

Why this matters

Multiple failures in a short time window indicate password guessing

Helps identify the account being targeted before compromise

Confirms suspicious behavior even if access was not yet successful
All failed attempts targeted the same user account (martin_kedob)

Attempts originated from a single internal IP address

Multiple destination ports were used, indicating automated behavior

This activity directly preceded a successful SSH login
