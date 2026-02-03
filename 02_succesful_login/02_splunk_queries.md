# Detection – Successful SSH Authentication

### Primary Splunk Query

```spl
index=main sourcetype=linux_secure "Accepted password

What this query shows

This query detects successful SSH authentication events.
It confirms that the attacker successfully authenticated after multiple failed attempts.

Investigation notes

User account accessed: martin_kedob

Authentication method: password-based SSH

Source IP observed after brute-force attempts

Confirms transition from attempted access to confirmed compromise

Supporting Query
index=main sourcetype=linux_secure sshd
