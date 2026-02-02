### Primary Detection Query
```spl
index=main sourcetype=linux_secure "Failed password"
index=main sourcetype=linux_secure sshd
index=main sourcetype=linux_secure "Failed password" | stats count by src_ip user

