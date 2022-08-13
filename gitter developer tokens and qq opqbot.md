---
title: gitter developer tokens and qq opqbot
created: '2022-08-13T00:54:17.441Z'
modified: '2022-08-13T07:45:44.808Z'
---

# gitter developer tokens and qq opqbot

关于自动加群 可以考虑使用安卓手机自启动功能（需要下载[startup manager]()， 有root权限） 用[termux-appium] 自动操作手机在联网的情况下自启动加群

现在有两个标准[onebot]() [nonebot](https://nb2.baka.icu/)
 这两个协议都不支持主动加好友 加群 还有收红包方法 至少mac qq协议支持这些方法 但是其他的协议比如手表 ipad协议支不支持就不清楚了

onebot有大量的[qq适配器]() 而nonebot有[大量的插件和除了qq以外的连接器](https://nb2.baka.icu/store)

nonebot可以[连接onebot](https://onebot.adapters.nonebot.dev/docs/guide/installation)

在onebot的qq适配器中 [oicq](https://github.com/takayama-lily/oicq)这个适配器有在群里面加好友的方法`addFriend(gid, uid)`可以参考,提供了一些用于逆向qq协议的程序：

[txhook](https://github.com/fuqiuluo/TXHook) 该软件适合在安卓8.0以上系统运行，理论支持安卓7.0以上，但是很多问题。群号：901422091 702991373
- 获取ShareKey\PublicKey\D2\A2...
- 主动拦截固定Ecdh密钥及版本
- 对Jce\Protobuf的自动分析
- 过滤抓包，支持高级过滤（长按抓包页面的搜索栏展示/隐藏图标）

[protobuf online decode](https://protobuf-decoder.netlify.app)
[protobuf unpack-tools](https://github.com/takayama-lily/unpack-tools)

也有一些可以进行二次开发的[qq web api](https://github.com/takayama-lily/oicq/blob/main/web-api.md) 搜索QQ号和群号 且有个性签名等更多信息 或许可以搜索关键词？

这些适配器中有的提供了qq频道的支持：

[oicp-guild](https://github.com/takayama-lily/oicq-guild)

也可以考虑用frida ghidra [radare2](https://rada.re/n/radare2.html) cutter来[逆向opqbot的go编译好了的程序](https://cn.bing.com/search?q=reverse+go+binary&form=CHRDEF&sp=-1&pq=reverse+go+binary&sc=0-17&qs=n&sk=&cvid=3A1FCCCF9C2F495DB516CB656D281DCA&ghsh=0&ghacc=0&ghpl=) 或者逆向分析opqbot的网络请求数据 甚至直接动态调用opqbot里面的方法 直接用其他机器人登陆之后获得的cookie进行操作

to get the token, login first, then visit [here](https://developer.gitter.im/apps) or click "sign in" [here](https://developer.gitter.im/)

据说扫码登录只支持同一个ip下面的登陆 不知道为什么这个opqbot登陆失败 但是其他机器人都提供了账号密码登陆的渠道 将opqbot的协议逆向出来 或许可以提高登陆成功率 实现相同的功能

默认(可修改)在 ./data/your-account/ 下会自动生成device.json设备文件，登录完成后此设备文件长期有效
设备文件的生成并非随机，而是使用固定算法，一个账号会永远生成同一份设备文件
如果需要在异地服务器上登录，建议先在常用地通过设备验证并登录挂机一段时间
由于会生成相同设备文件，只要不手动修改，只需验证一次，在任何地区都可直接登录


it seems the login issue of opqbot is related to the account itself, not gitter token, software version or proxy

by the way we could always use go-cqhttp, without the ability to collect red packet and add group/friends.

qq add group/friends may be enabled by our windows virtual machines. without opq, it is very memory intensive.

tokens:
```
74eb7eb14aa36d1b9c2c663bc49335e8becd5318
```
```
2d391bd7639362032d09abfc5a9cc6368b7664d5
```
```
bdf52599d992665509ee5b0b533d5eed08452def
```
