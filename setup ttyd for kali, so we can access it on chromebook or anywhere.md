---
title: 'setup ttyd for kali, so we can access it on chromebook or anywhere'
created: '2022-12-07T16:06:39.931Z'
modified: '2022-12-07T16:08:39.809Z'
---

# setup ttyd for kali, so we can access it on chromebook or anywhere

i don't think this will work on android, but let's see?

```bash
ttyd -p <port> -i <interface> -c <username>:<password>
```
