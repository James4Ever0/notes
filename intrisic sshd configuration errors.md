---
created: 2024-06-23T11:11:02+08:00
modified: 2024-06-23T11:14:51+08:00
---

# intrisic sshd configuration errors

On latest Ubuntu 24.04 the sshd config includes files under `/etc/ssh/sshd_config.d` which has a file named `50-cloud-init.conf` has the line overriding any other setting afterwords.

```config
PasswordAuthentication yes
```

You need to change both `/etc/ssh/sshd_config` and this file to disable password authentication.
