---
created: 2022-03-04T23:13:13+08:00
modified: 2022-03-05T18:11:46+08:00
---

# Worth Trying Remote Computer Connection

NoMachine NX
Moonlight for NVIDIA Windows
parsec for windows/macos host
ssh-rdp for linux host/client

somehow usable on localhost:

x11vnc -localhost -display :0 -threads -forever
vncviewer -PreferredEncoding=ZRLE localhoat:0
