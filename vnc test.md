---
title: vnc test
created: '2022-08-09T18:42:03.499Z'
modified: '2022-08-09T18:46:11.185Z'
---

# vnc test

password: 472831

commands:
```bash
export XAUTHORITY=/root/.Xauthority
export DISPLAY=:1
# kill previous running x11vnc
joker list | grep x11vnc | awk '{print $1}' | xargs -iabc kill -s KILL abc
# launch new vnc
joker x11vnc -threads -forever -rfbauth /root/.vnc/passwd
```
