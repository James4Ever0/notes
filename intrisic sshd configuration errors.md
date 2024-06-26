---
title: intrisic sshd configuration errors
created: '2024-06-23T03:11:02.000Z'
modified: '2024-06-27T01:56:35.887Z'
---

# intrisic sshd configuration errors

if you want to use ssh port forwarding as systemd service, keep in mind that the default user for execution is root, and you need to use the public key of root to login.

or you can change the user executing the task in service config:

```systemd
[System]
User=xxx
```

---

[`chisel`](https://github.com/jpillora/chisel) can be used for port forwarding by http compared with `wstunnel`, able to survive `nginx` (still need to configure websocket upgrades).

```bash
# server, allowing reverse port forwarding
chisel server -p <port> --auth <user>:<pass> --reverse

# client
chisel client --auth <user>:<pass> <protocol>://<url> <local_addr>:<remote_addr> R:<remote_addr>:<local_addr>
```

---

if you want to have multiple host sharing same ip because of proxy forwarding or different network locations, then you need to change the system host mapping file.

in linux and macos it is at `/etc/hosts`

in windows, `C:\Windows\System32\drivers\etc\hosts`

you need to configure the host file on the proxy machine if you want to avoid name clashes with proxies. these host names can be less informative to hide the intent.

---

on latest ubuntu 24.04 the sshd config includes files under `/etc/ssh/sshd_config.d` which has a file named `50-cloud-init.conf` has the line overriding any other setting afterwords.

```config
PasswordAuthentication yes
```

you need to change both `/etc/ssh/sshd_config` and this file to disable password authentication.

---

`-R` will not allow you to open `0.0.0.0` port on remote machine unless you configure something in `/etc/ssh/sshd_config` like below.

```config
AllowTcpForwarding yes
GatewayPorts clientspecified
```

if not, use `socat` to finally deliver the forwarded remote local port to remote public port.

```bash
socat TCP-LISTEN:<lport>,reuseaddr,fork TCP:<rhost>:<rport>
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
