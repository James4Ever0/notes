---
title: vnc test
created: '2022-08-09T18:42:03.499Z'
modified: '2022-08-09T18:47:01.033Z'
---

# vnc test

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
