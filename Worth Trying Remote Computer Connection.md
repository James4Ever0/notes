---
tags: [remote control, remote desktop]
title: Worth Trying Remote Computer Connection
created: 2022-03-04T15:13:13+00:00
modified: 2024-07-08T14:18:48+08:00
---

# Worth Trying Remote Computer Connection

for hardware kvm over ip, there is pikvm swite for turning rpi3b+ into ipkvm and armkvm series that are dedicated low cost ipkvm hardwares.

---

to persist ssh connection:

```bash
ssh -o ControlMaster=auto -o ControlPersist=yes -o BatchMode=yes user@hostname
```

---

ssh port forwarding:

```bash
# requires sudo
sudo ssh -v -N -L <local_addr>:<remote_addr> -R <remote_addr>:<local_addr> <user>@<remote_host>
```

remote or local address must at least have port number specified, optionally with host address like: `[host]:<port>`

`-L` opens a local port at local address and forward to remote address. `-R` opens a remote port at remote address and forward to local address. `-N` disable the tty connection. `-v` shows the debug info.

---

enable pubkey authentication for nomachine:

first generate the key with `ssh-keygen`, copy your pubkey content at `.ssh/id_rsa.pub` (local host) to remote host at `~/.nx/config/authorized.crt`, one pubkey per line.

next change the setting `AcceptedAuthenticationMethods` as `NX-private-key` in file `/usr/NX/etc/server.cfg` at remote host.

no need to restart the service. change your connection method to key based authentication and select the private key file path.

---

NoMachine NX

FreeNX

Moonlight for NVIDIA Windows

parsec for windows/macos host

ssh-rdp for linux host/client

somehow usable on localhost:

x11vnc -localhost -display :0 -threads -forever

vncviewer -PreferredEncoding=ZRLE localhoat:0

sunshine host for windows/linux

https://github.com/SunshineStream/Sunshine/blob/master/README.md#macos

https://github.com/loki-47-6F-64/sunshine

openstream-server a fork of sunshine

https://open-stream.net/

synergy mouse keyboard sharing tool

ssh -X/-Y allowX11forwarding

hardware solution: kvm switch (high grade with audio redirection separate usb ports)
