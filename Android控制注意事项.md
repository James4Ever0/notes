---
title: Android控制注意事项
created: '2024-03-31T04:16:04.992Z'
modified: '2024-03-31T12:13:40.518Z'
---

# Android控制注意事项

长时间不开机的机器可能会发生时间错位问题 需要用adb进行时间校准

```bash
adb shell date "YYYY-MM-DD HH:MM:SS"
# sometimes you have to use '-s' flag
```

把所有闹钟都关闭 防止关了机又打开 或者在脚本操作控制的时候出问题

---

建议使用云手机平台(搜索：开源云手机)，虚拟手机，方便进行环境打包和重新部署。

redroid supports adb connection, and is a docker image

[redroid-doc](https://github.com/remote-android/redroid-doc) and [redroid tutorial](https://www.dsx2020.com/homelab-mini-host-x86-docker-deploys-open-source-cloud-phone-android-redroid/)

[lamda](https://github.com/rev1si0n/lamda) is a multi-source (simulator and real device support) android controlling, network capturing and reverse engineering platform

[lamda wiki](https://github.com/rev1si0n/lamda/wiki)

---

如果adb出现连接问题，可以重启adb服务

usb硬件出问题一般是因为供电不足，或者连接线接触不良。所以可以加强供电，以及更换更好的连接线。

```bash
adb kill-server
adb start-server
```
