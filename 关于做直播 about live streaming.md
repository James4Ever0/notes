---
title: 关于做直播 about live streaming
created: '2022-10-21T14:09:58.000Z'
modified: '2022-10-22T15:18:17.341Z'
---

# 关于做直播 about live streaming

## 用第三方软件推流 obs

[b站官方开播页面 可以获取obs推流链接](https://link.bilibili.com/p/center/index#/my-room/start-live)



## 渲染chat room使用的工具

需要能够播放视频 放置图片素材 但是其实这个图片可以放到一边去 放到专门的broadcast里面

为了好看你可以专门选择现成的聊天渲染库 记得及时清理 然后要用ffmpeg把xvbf的画面转为rtmp

[owncast](https://github.com/owncast/owncast) with live streaming support

## 随想

a nas or a huge raid-n array to store a huge amount of previous live streaming recordings, only stream recordings 1 month ago

a powerful server for preprocessing, postprocessing

send the response to the most plausible group, likely to fit into the context.

过滤群聊里面的广告内容（包括机器人自己发出去的广告内容） 色情 暴恐 声音不对劲要去掉 合适的BGM

直播上传带宽要保证 延迟要低

"聚合直播"

做直播最重要的就是互动性

你可以直播群友聊天的画面 要去掉个人隐私的头像 信息 要过滤掉nsfw的内容 操作qq机器人来和群友说话 或者让送礼物最多的人获得发言权 排行榜最上面的人获得发言权 群聊也不一定要单一 多个群一起弄 甚至多个社交软件一起弄 群聊私聊一起用

你也可以参考其他的主播 看看他们是怎么做的

可以通过分析评论 切换直播主题 切换直播画面


## 随想

Yukio 22:29:44
我直播群友聊天咋样？

Yukio 22:30:07
我直播群友聊天 然后给我留言的人 有机会把消息发到群里面来

Yukio 22:30:30
其中送礼物送的最多的发消息发进来的概率最大

Yukio 22:31:49
不仅如此 我还多个群聚合聊天 多社交软件 多语言聚合聊天

Yukio 22:32:06
我还可以自由切换话题 自动翻译

Yukio 22:32:36
也就是说如果你和外国人聊天 你说中文变英文

Yukio 22:32:46
别人说英文变中文

黑暗骑士 22:33:20
直播看你装奈子

Yukio 22:33:33
nsfw不能直播

Yukio 22:33:45
直播最重要的是互动啊

Yukio 22:33:51
播其他的也行

Yukio 22:34:06
但是装柰子 也得sfw

Yukio 22:34:19
所以有可能需要打码

Yukio 22:34:29
检测出来nsfw区域 自动打码

Yukio 22:34:36
或者全屏打码

Yukio 22:35:07
你说什么 我可以给你在线搜索视频给你看

Yukio 22:35:49
你不说话的时候我就挑热门视频和热门直播转发

Yukio 22:36:15
根据进来的观众们的历史观看记录和历史发言来播视频

Yukio 22:42:38
这个换台的话 本人三分钟可以撤销两次

Yukio 22:43:09
而其他人在本人获得换台权利之后 三分钟之后才能继续排队

Yukio 22:43:23
早就不招了

Yukio 22:44:29
你建的话 我有过滤器啊

Yukio 22:44:32
你可以建

Yukio 22:44:57
但是要是有关键字 我这边不会播你的

Yukio 22:45:08
而且头像和昵称

Yukio 22:45:13
不会有

Yukio 22:46:05
如果sfw

Yukio 22:46:14
那么就是不够涩

Yukio 22:46:18
也不会有问题

Yukio 22:46:40
再说了

Yukio 22:46:51
让别人跟你聊天不是好事么

Yukio 22:47:16
取决于涩涩的程度
