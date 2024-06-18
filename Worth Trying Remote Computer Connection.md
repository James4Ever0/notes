---
tags: [remote control, remote desktop]
title: Worth Trying Remote Computer Connection
created: '2022-03-04T15:13:13.000Z'
modified: '2024-06-18T09:13:23.789Z'
---

# Worth Trying Remote Computer Connection

ssh port forwarding:

```bash
ssh -v -N -L <local_addr>:<remote_addr> -R <remote_addr>:<local_addr> <user>@<remote_host>
```

remote or local address must at least have port number specified, optionally with host address like: `[host]:<port>`

`-L` opens a local port at local address and forward to remote address. `-R` opens a remote port at remote address and forward to local address. `-N` disable the tty connection. `-v` shows the debug info.

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
