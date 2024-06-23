---
created: 2024-06-23T11:11:02+08:00
modified: 2024-06-24T01:01:29+08:00
---

# intrisic sshd configuration errors

on latest ubuntu 24.04 the sshd config includes files under `/etc/ssh/sshd_config.d` which has a file named `50-cloud-init.conf` has the line overriding any other setting afterwords.

```config
PasswordAuthentication yes
```

you need to change both `/etc/ssh/sshd_config` and this file to disable password authentication.

---

`-R` will not allow you to open `0.0.0.0` port on remote machine unless you configure something in `/etc/ssh/sshd_config` like below. if not, use `socat` to finally deliver the forwarded remote local port to remote public port.

```config
AllowTcpForwarding yes
GatewayPorts clientspecified
```

---

port forwarding failure can be corrected.

```bash
# get the process pid of the port
sudo lsof -i :<port>
lsof -i :<port>
# kill the process
kill <port>
# rerun lsof to check if the port is freed
```

---

`n2n` can be in handy if you do not have too many ports on internet and still want to access all ports in between your local machines.

---

if connection is unstable, use `-o ServerAliveInterval=60 -o ServerAliveCountMax=3` to extend the timeout period.
