---
created: 2022-03-04T23:13:13+08:00
modified: 2022-03-06T16:58:33+08:00
---

# Worth Trying Remote Computer Connection

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
