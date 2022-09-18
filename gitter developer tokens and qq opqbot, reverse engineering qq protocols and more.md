---
tags: [chatbot, chatbot framework, opqbot, pyjom, qq, reverse engineering, stub]
title: gitter developer tokens and qq opqbot, reverse engineering qq protocols and more
created: 2022-08-13T08:54:17+08:00
modified: 2022-09-18T16:02:20+08:00
---

# gitter developer tokens and qq opqbot, reverse engineering qq protocols and more

qq seems to release mac qq with electron, great easier for reverse engineering

[how to reverse go binary, golang reverse](https://zu1k.com/posts/security/reverse/golang-reverse/)

opqbot官方已经说了 登陆过程中会用到远程的服务器 这个服务器究竟在干什么不得而知 可能和登陆有关也可能没有关系 但是服务器维护期间是没法扫码登录的 如果有可以正常使用的secdata是可以直接启动服务的 不需要服务器 所以估计这个服务器很可能就是拿来解析cookie的

login error:
```
2022/08/14 00:01:24.808 [I]  Scan Status 48 Uin 0 
2022/08/14 00:01:25.880 [I]  Scan Status 48 Uin 0 
2022/08/14 00:01:26.937 [I]  Scan Status 53 Uin 0
2022/08/14 00:01:27.998 [I]  Scan Status 53 Uin 0 
2022/08/14 00:01:29.054 [N]  User <userId> 登录中..请勿连续操作,登录成功后或释放连接后在继续操作 登陆成功后请勿频繁扫码再次登陆(除非冻结导致的掉线) 发不出去群消息请挂机几天 TX日常风控
=========本框架 🎈 免费 🎈 使用 谨防 ⚠️ 诈骗 ⚠️ 收费 切勿用于 🈲️ 非 🈲️ 法用途
=========交流群:757360354 TG群组:https://t.me/IOTQQ      
=========开源社区 👍 https://github.com/opq-osc 👍       
=========项目主页 😄 https://github.com/OPQBOT/OPQ/wiki 😄
=========项目Wiki 📒 https://github.com/OPQBOT/OPQ/wiki 📒
2022/08/14 00:02:30.234 [W]  recvPump session 0D48F5949075DA13D3A9F83838903920
2022/08/14 00:02:30.234 [A]  Default Closed:0D48F5949075DA13D3A9F83838903920
2022/08/14 00:02:30.235 [D]  Unregister In Conn -> 0D48F5949075DA13D3A9F83838903920
```

关于自动加群 可以考虑使用安卓手机自启动功能（需要下载[startup manager](https://play.google.com/store/apps/details?id=imoblife.startupmanager) 或者[boot manager](https://play.google.com/store/apps/details?id=de.defim.apk.bootmanager&showAllReviews=true)（有root权限和xposed框架）） 用[termux-appium](https://www.npmjs.com/package/termux-appium) 自动操作手机在联网的情况下自启动加群

现在有两个标准[onebot](https://onebot.dev/) [nonebot](https://nb2.baka.icu/)

这两个协议都不支持主动加好友 加群 还有收红包方法 至少mac qq协议支持这些方法 但是其他的协议比如手表 ipad协议支不支持就不清楚了

onebot有大量的[qq适配器](https://onebot.dev/ecosystem.html#onebot-12) 而nonebot有[大量的插件和除了qq以外的连接器](https://nb2.baka.icu/store)

nonebot可以[连接onebot](https://onebot.adapters.nonebot.dev/docs/guide/installation)

在onebot的qq适配器中 oicq可以查看qq历史聊天记录（有待验证） 可能对qq的数据爬取有帮助 视频爬取 [oicq](https://github.com/takayama-lily/oicq)这个适配器有在群里面加好友的方法`addFriend(gid, uid)`可以参考,提供了一些用于逆向qq协议的程序：

[txhook](https://github.com/fuqiuluo/TXHook) 该软件适合在安卓8.0以上系统运行，理论支持安卓7.0以上，但是很多问题。群号：901422091 702991373
- 获取ShareKey\PublicKey\D2\A2...
- 主动拦截固定Ecdh密钥及版本
- 对Jce\Protobuf的自动分析
- 过滤抓包，支持高级过滤（长按抓包页面的搜索栏展示/隐藏图标）

[protobuf online decode](https://protobuf-decoder.netlify.app)
[protobuf unpack-tools](https://github.com/takayama-lily/unpack-tools)

也有一些可以进行二次开发的[qq web api](https://github.com/takayama-lily/oicq/blob/main/web-api.md) 搜索QQ号和群号 且有个性签名等更多信息 或许可以搜索关键词？

这些适配器中有的提供了qq频道的支持：

[oicq-guild](https://github.com/takayama-lily/oicq-guild)

也可以考虑用[frida](https://frida.re/) [ghidra](https://github.com/NationalSecurityAgency/ghidra) [radare2](https://rada.re/n/radare2.html) [cutter](https://cutter.re/)来[逆向opqbot的go编译好了的程序](https://cn.bing.com/search?q=reverse+go+binary&form=CHRDEF&sp=-1&pq=reverse+go+binary&sc=0-17&qs=n&sk=&cvid=3A1FCCCF9C2F495DB516CB656D281DCA&ghsh=0&ghacc=0&ghpl=) 或者逆向分析opqbot的网络请求数据 甚至直接动态调用opqbot里面的方法 直接用其他机器人登陆之后获得的cookie进行操作

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
