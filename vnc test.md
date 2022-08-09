---
title: vnc test
created: '2022-08-09T18:42:03.499Z'
modified: '2022-08-09T18:43:07.590Z'
---

# vnc test

password: 472831

commands:
```bash
export XAUTHORITY=/root/.Xauthority
export DISPLAY=:1
x11vnc -threads -forever -rfbauth /root/.vnc/passwd
```
