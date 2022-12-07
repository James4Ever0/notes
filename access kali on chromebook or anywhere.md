---
title: access kali on chromebook or anywhere
created: '2022-12-07T16:06:39.931Z'
modified: '2022-12-07T18:47:09.925Z'
---

# access kali on chromebook or anywhere

## setup ttyd

i don't think this will work on android, but let's see?

```bash
ttyd -p <port> -c <username>:<password> <shell_path>
# don't specify interface since that will screw things up
```

## setup x11vnc and novnc

x11vnc is mirroring the current x11 session. i set it without password.


