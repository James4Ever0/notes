---
title: Android控制注意事项
created: '2024-03-31T04:16:04.992Z'
modified: '2024-03-31T04:34:05.244Z'
---

# Android控制注意事项

长时间不开机的机器可能会发生时间错位问题 需要用adb进行时间校准

```bash
adb shell date "YYYY-MM-DD HH:MM:SS"
# sometimes you have to use '-s' flag
```

把所有闹钟都关闭 防止关了机又打开 或者在脚本操作控制的时候出问题

建议使用云手机平台，虚拟手机，方便进行环境打包和重新部署。

如果adb出现连接问题，可以重启adb服务

```bash
adb kill-server
adb start-server

```
