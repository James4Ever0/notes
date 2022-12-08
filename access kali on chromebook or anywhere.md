---
title: access kali on chromebook or anywhere
created: '2022-12-07T16:06:39.931Z'
modified: '2022-12-08T05:23:03.016Z'
---

# access kali on chromebook or anywhere

## setup tty

i don't think this will work on android, but let's see?

```bash
ttyd -p <port> -c <username>:<password> <shell_path>
# don't specify interface since that will screw things up
```

## setup x11vnc and novnc

notice novnc has clipboard function now. share clipboard content across devices via the sidebar menu,

in reference of [kali official](https://kali.org/general-use/novnc-kali-in-browser)

x11vnc is mirroring the current x11 session. i set it without password.

```bash
#retrieved from fish history
x11vnc -threads -forever
```

then launch novnc server
```bash
novnc  --vnc localhost:5900 --listen 10020
```

use this url to access from chromebook:
```
http://<kali_ip>:10020/vnc.html?host=<kali_ip>&port=10020
```

