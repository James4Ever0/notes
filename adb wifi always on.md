---
title: adb wifi always on
created: '2022-11-04T01:10:42.000Z'
modified: '2022-11-04T01:40:57.569Z'
---

# adb over wifi always on

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

set things under `/data/adb/services.d/` and make them executable

```bash
mount -o remount,rw /
# then you can modify /sytem/etc/init.d, but not /system/bin cause it is a copy of /data/system/bin. you should create script there.
```

create this under `/system/etc/init.d/`

```bash
service adb_wifi_enable /system/bin/adb_wifi_enable.sh
    disabled
    oneshot
    seclabel u:r:magisk:s0

on property:sys.boot_completed=1
    start adb_wifi_enable
```
