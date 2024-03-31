---
title: Android控制注意事项
created: '2024-03-31T04:16:04.992Z'
modified: '2024-03-31T04:17:41.495Z'
---

# Android控制注意事项

长时间不开机的机器可能会发生时间错位问题 需要用adb进行时间校准

```bash
adb shell date -s "YYYY-MM-DD HH:MM:SS"
```
