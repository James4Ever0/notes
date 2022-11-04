---
created: 2022-11-04T09:10:42+08:00
modified: 2022-11-04T09:13:24+08:00
---

# adb wifi always on

warning: could be dangerous cause adb remote connections seem without any password. consider protect that with some proxy.

turning on:

```bash
setprop service.adb.tcp.port 5555
stop adbd
start adbd
```
