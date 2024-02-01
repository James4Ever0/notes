---
title: Telegram 闪退修复
created: '2024-02-01T11:30:37.482Z'
modified: '2024-02-01T11:32:14.312Z'
---

# Telegram 闪退修复

电报偶然一次打开了一个莫名其妙的图片 然后导致每次打开都崩溃

用root权限 在`/data/data/org.telegram.messaging/`下面删除`cache4.db`

