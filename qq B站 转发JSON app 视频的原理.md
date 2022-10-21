---
created: 2022-10-18T15:52:52+08:00
modified: 2022-10-21T20:40:20+08:00
---

# qq B站 转发JSON app 视频的原理

## 打赏 e-begging

Yukio 20:36:09
帮忙百度 然后时不时发个打赏链接

Yukio 20:36:22
涩图里面加赞助二维码


## 通用发广告策略

Yukio 16:06:23
我在想 用GIF怎么引流

Yukio 16:06:50
GIF不让你扫码 所以说只能GIF下面放个链接

Yukio 16:07:30
GIF下面可以放二维码？

Yukio 16:07:41
都可以试试 反正不吃亏

Yukio 16:17:17
狗子狗叫太吵了

Yukio 16:17:33
转成GIF感觉会效果好点

Yukio 16:19:26
我甚至可以直接ugc当成封面 然后下面发链接引流

## 逆向qq安卓版

Yukio 15:51:01
我最近研究了一下b站转发QQ群的原理

Yukio 15:51:01
QQ群里面只能发一种JSON

Yukio 15:51:02
里面有个token看起来像是checksum

Yukio 15:51:02
所以JSON里面稍作改动就发不出去了

Yukio 15:51:02
不过如果你可以拦截安卓的intent 用frida拦截生成这个JSON的call 可能可以生成任意的JSON
