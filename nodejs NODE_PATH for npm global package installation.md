---
title: nodejs NODE_PATH for npm global package installation
created: '2022-12-10T13:29:15.916Z'
modified: '2022-12-10T13:34:14.537Z'
---

# nodejs NODE_PATH for npm global package installation

when installing global ackages, we do not need to specify NODE_PATH. but it is not configured beforehand thus when you want to import packages from there you will face issue.

for bash/fish:

```bash
export NODE_PATH=<NODE_PATH>
```

chech the exact path of `NODE_PATH` after invoking `npm install -g <package_name>`, then check if the installed package exists in that path you guessed.

on termux: `/data/data/com.termux/files/usr/lib/node_modules`

on kali: `/usr/local/lib/node_modules` (may be inaccurate)

on macos: `` (nodejs installed via brew)

