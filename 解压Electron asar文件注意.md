---
title: 解压Electron asar文件注意
created: '2024-03-31T05:28:07.202Z'
modified: '2024-03-31T05:28:34.275Z'
---

# 解压Electron asar文件注意

解压asar的时候 注意不要移动`app.asar`的位置 解压完毕之后再移动

```bash
# to prevent 'unable to find xxx in app.asar.unpacked' issue, do not move app.asar yet.
asar e app.asar app
mkdir asar
cp app.asar asar
rm app.asar
```

