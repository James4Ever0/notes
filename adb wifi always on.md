---
created: 2022-11-04T09:10:42+08:00
modified: 2022-11-04T09:18:48+08:00
---

# adb wifi always on

warning: could be dangerous cause adb remote connections seem without any password. consider protect that with some proxy.

turning on:

```bash
setprop service.adb.tcp.port 5555
stop adbd
start adbd
```
turning off:

```bash
setprop service.adb.tcp.port -1
stop adbd
start adbd
```

set things under `/data/adb/services.d/`

```bash
mount -o remount,rw /
```

create this under `/system/etc/init.d/`
