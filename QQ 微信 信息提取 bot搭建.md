---
tags: [chatbot, conversation, information gathering, pyjom, scraping, video generator]
title: QQ 微信 信息提取 bot搭建
created: '2022-05-24T05:30:47.000Z'
modified: '2022-08-18T07:49:16.823Z'
---

# QQ 微信 信息提取 bot搭建

qq聊天记录导出 qq消息导出

[微信聊天记录导出](https://github.com/ppwwyyxx/wechat-dump)

聊天记录渲染成图片 render chat record to picture
conclusion so far: people like to use vue to recreate popular interfaces, and you may grab some interface from it.
[vue-wechat](https://github.com/useryangtao/vue-wechat)
[🔥 基于Vue2.0高仿微信App的单页应用](https://github.com/zhaohaodang/vue-WeChat)
[vue-qq](https://github.com/lensh/vue-qq)
[一个长得像QQ的demo](https://github.com/lensh/vue-qq)
[vue qq 聊天界面组件库](https://blog.csdn.net/weixin_45783387/article/details/121595190)
```bash
npm install vue-mchat
```
[vue 本项目是一个在线聊天系统，最大程度的还原了Mac客户端QQ。](https://github.com/likaia/chat-system)
[vue-miniQQ————基于Vue2实现的仿手机QQ单页面应用](https://github.com/jiangqizheng/vue-MiniQQ)
[基于Vue2实现的单页面应用 qq界面模仿](https://github.com/lvzhenbang/vue2-qq)
[demo大师 qq界面模仿 vuejs 要钱](http://www.demodashi.com/demo/12539.html)
[demo大师 vue3 仿微信/qq界面 免费](http://www.demodashi.com/demo/17893.html)
[render chat record to picture 微信聊天记录渲染成图片](https://github.com/ppwwyyxx/wechat-dump/blob/master/dump-html.py)
[html css渲染](https://blog.csdn.net/weixin_42298415/article/details/117871213)
[仿QQ android的聊天界面](https://github.com/zb-tjw/imooc_tuling)
[HTML5手机微信聊天界面代码](https://blog.csdn.net/weixin_30745553/article/details/98240195)
[HTML5 WebSocket 仿微信界面的网页群聊演示Demo](https://gitee.com/ydq/WebChat?_from=gitee_search)
[用html5做的仿微信聊天界面](https://gitee.com/qjx378/wxchat?_from=gitee_search)
[基于H5技术实现的在线聊天室APP](https://github.com/helpcode/chat-room)
[Simple chatbot exercise using only JavaScript, HTML, CSS](https://github.com/sylviapap/chatbot)
[Multi-Room Chat Application](https://github.com/uditalias/chat-nodejs)
[一个基于AngularJS、NodeJS、Express、socket.io搭建的在线聊天室。](https://github.com/sheila1227/ChatRoom-AngularJS)
[facebook like chatroom](https://github.com/shaadomanthra/facebook-like-chat)

qq空间发美女图片把人家的脸要挡住 或者要把脸换了 或者直接使用live2d three.js 甚至3d的渲染模型来把脸给它挡住

somehow the wechat web uos protocol is usable again? check it out.

https://www.npmjs.com/package/wechaty-puppet-wechat
https://github.com/wechaty/puppet-wechat/pull/206

would it be a lot easier if we can send those article/video links to external (out of gfw) social media platforms in their native language? still censorship will be applied.

wechat frida hook on macos:
https://github.com/dounine/wechat-frida

WeChat PC Frida hook:
https://github.com/K265/frida-wechat-sticker
https://github.com/kingking888/frida_wechat_hook

## qq号码注册规则

qq群最多可以添加500个群 1500个好友 其中群可加的数量 = max(0,500 - 已加入群数量 - 好友数量)
可以退出一些安静的群 不发红包的群 删除好友

屏蔽别人加我为好友 允许别人拉我进群 自动退出广告群 退出不活跃的群

群一天只能加两三个 或者手机上可以加十个
好友一天可以加三十几个

一个验证QQ群的Python代码
https://www.bilibili.com/read/mobile?id=10044756

frida inject mobile android qq and open qzone:
https://github.com/xhtechxposed/fridainjectqq

search https://qun.qq.com in search engines

可以考虑截图获取QQ群验证问题 或者手机测试 appium

if possible then just use frida/radare2 or some reverse engineering to automate the process.

radare2 -> rizin.re(radare2 fork) based, ida alike, with ghidra decompiler, reverse engineering tool:
https://cutter.re

如何获取进群验证问题？记得可以拦截PC端搜索QQ群接收的数据包获取验证问题 或许不行 总之可以获取到一些参数 查看是否包含验证问题 是不是允许任何人进群 也可以考虑拦截opqqq的通信 或者发送一些通用的加群验证信息 比如“加群学习” “小伙伴一起玩” 之类的 或者用ai模型根据群描述 群主题 生成

一个手机号码可以申请10个qq号，一个手机号绑定的QQ帐号名额上限为10个，但一天一个手机号只能成功注册两到三个

WeChat needs serious reverse engineering like frida.

https://github.com/cixingguangming55555/wechat-bot
有webapi的微信机器人 注入dll到pc

https://github.com/mrsanshui/WeChatPYAPI
可以加好友的python wechat pc hook

https://github.com/snlie/WeChat-Hook
易语言的wechat hook 功能非常全 搜索 加人 有教程链接 教学代码

https://github.com/TonyChen56/WeChatRobot
比较老的wechat逆向模块 wechatapis.dll半天获得不了 有教程链接

https://github.com/wechaty/puppet-xp
frida 驱动的wechat puppet 暂时没有加人 搜索人 在windows上运行

wechat reverse engineering tutorials:
https://github.com/hedada-hc/pc_wechat_hook
https://github.com/zmrbak/PcWeChatHooK

wechaty base framework:
https://github.com/Wechaty/python-wechaty/ (puppet support might be incomplete)
https://github.com/Wechaty/wechaty/

botoy opqbot api for python
https://botoy.opqbot.com/zh_CN/latest/action/

qq opqbot (for wechat it has rstbot) download and install (need gitter.im api token):
https://docs.opqbot.com/guide/manual.html#启动失败

opqbot needs to be reverse engineered or we won't know what is going on inside.

unofficial opqbot wiki:
https://mcenjoy.cn/opqbotwiki/

wechat bot(non-free wechat puppets):
wechaty

quoted content are controversial and highly viral. must be filtered and classified before proceeding.
quotes are like comments.
