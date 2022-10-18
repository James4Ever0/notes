---
created: 2022-10-18T15:52:52+08:00
modified: 2022-10-18T15:53:20+08:00
---

# qq B站 转发JSON app 视频的原理

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
