---
title: android packet capture
created: '2022-11-04T01:22:07.000Z'
modified: '2022-11-04T02:40:26.849Z'
---

# android packet capture

## disable ssl pinning

use frida scripts specific to applications

justtrustme xposed

sslunpinning xposed

[apk-mitm](https://github.com/shroudedcode/apk-mitm) by repacking apk and resigning

## capture, packet routing

recommend to use: [PCAPdroid-API](https://github.com/James4Ever0/PCAPdroid-API)

[PCAPdroid API reference](https://github.com/emanuele-f/PCAPdroid/blob/master/docs/app_api.md)

```bash
adb shell am start -e action start -e pcap_dump_mode udp_exporter -e collector_ip_address 127.0.0.1 -e collector_port 5123 -e app_filter com.tencent.mobileqq -n com.emanuelef.remote_capture.debug/com.emanuelef.remote_capture.activities.CaptureCtrl
```

setting up http proxy via adb:

```bash
# this does not ensure that the target app is captured.
adb shell settings put global http_proxy <address>:<port>
```
