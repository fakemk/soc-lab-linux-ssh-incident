## Detection – Successful SSH Authentication

## Primary Detection Query

```spl
index=main sourcetype=linux_secure "Accepted password"
What this shows

Successful SSH authentication events recorded by sshd

Confirmation that valid credentials were used to access the system

Transition from failed authentication attempts to successful login

Investigation notes

User account accessed: martin_kedob

Authentication method: password-based SSH

Source IP observed after previous failed login attempts

Confirms movement from attempted access to confirmed compromise
Supporting Query
index=main sourcetype=linux_secure sshd

Why this matters

Successful authentication after repeated failures indicates credential compromise

Marks the point where the attacker gained interactive access to the host

Enables all subsequent post-compromise actions
