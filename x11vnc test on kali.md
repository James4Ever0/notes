---
tags: [credential, remote control, stub, test, VNC]
title: x11vnc test on kali
created: '2022-08-09T18:42:03.499Z'
modified: '2022-08-18T08:02:58.595Z'
---

# x11vnc test on kali

better use nomachine instead, which is based on nx

password: 472831

commands:
```bash
# necessary env for gui target, though may not suitable for xvfb
export XAUTHORITY=/root/.Xauthority
export DISPLAY=:1
# kill previous running x11vnc, if exists
joker list | grep x11vnc | awk '{print $1}' | xargs -iabc kill -s KILL abc
# launch new vnc
joker x11vnc -threads -forever -rfbauth /root/.vnc/passwd
```
