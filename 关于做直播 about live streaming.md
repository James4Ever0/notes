---
title: 关于做直播 about live streaming
created: '2022-10-21T14:09:58.000Z'
modified: '2022-12-12T19:43:34.514Z'
---

# 关于做直播 about live streaming

## run python in browser

[pyodide](https://python-in-browser.com/)

[pyscript](https://coderoasis.com/run-python-in-the-web-browser/)

[skulpt](http://skulpt.org/)

## pass parameter via url

[get url anchor text](https://programming.bogdanbucur.eu/how-to-get-the-url-anchor-with-javascript/)

you can still use query string when visiting github.io

```javascript
function getQueryStringValues(key) {
    var arrParamValues = [];
    var url = window.location.href.slice(window.location.href.indexOf('?') + 1).split('&');
 
    for (var i = 0; i < url.length; i++) {
        var arrParamInfo = url[i].split('=');
 
        if (arrParamInfo[0] == key || arrParamInfo[0] == key+'[]') {
            arrParamValues.push(decodeURIComponent(arrParamInfo[1]));
        }
    }
 
    return (arrParamValues.length > 0 ? (arrParamValues.length == 1 ? arrParamValues[0] : arrParamValues) : null);
}
```

## 保存粉丝cookie 避免接入xpay之后反复输入地址

[set and get a cookie with javascript](https://www.tutorialspoint.com/How-to-set-a-cookie-and-get-a-cookie-with-JavaScript)

## 付钱兑换礼物

要能够有效识别付钱的对象 用浏览器的cookie 送达目标地址

过滤人名

过滤群聊里面的广告内容 色情 暴恐 声音不对劲要去掉 合适的BGM

直播上传带宽要保证 延迟要低

"聚合直播"

做直播最重要的就是互动性

你可以直播群友聊天的画面 要去掉含有个人隐私的头像或照片 信息 QQ Email 要过滤掉nsfw的内容 操作qq机器人来和群友说话 或者让送礼物最多的人获得发言权 排行榜最上面的人获得发言权 群聊也不一定要单一 多个群一起弄 甚至多个社交软件一起弄 群聊私聊一起用

你也可以参考其他的主播 看看他们是怎么做的

可以通过分析评论 切换直播主题 切换直播画面

## 免签支付 获取订单号 给粉丝发福利 VIP

[b站充电API](https://github.com/SocialSisterYi/bilibili-API-collect/blob/be65d5f05b8024acf2b34c583a5d66144ec3c141/electric/WeChat&Alipay.md)

https://www.yunmianqian.com
https://github.com/assimon/easymqpay
https://github.com/szvone/vmqphp
https://github.com/wxs2/xposed-pay

https://github.com/szvone/vmqApk

[vmqapk 最新修改版](https://github.com/zwc456baby/vmqApk)

[xpay](https://github.com/Exrick/xpay) 这个东西需要人工监听 跪了

## 随想 8

视频广告

Yukio 21:46:07
应该来个淡入淡出之类的

Yukio 21:46:25
还有一个试看结束的提示

Yukio 21:46:37
试看开始之前的提示

播放视频内容也要有提示 开头和结尾要给人知道这个截取的片段是干什么的

## 随想 7

Yukio 01:56:43
付了款 留下联系方式 给你发福利

Yukio 01:57:16
但是万一有些人滥用呢

Yukio 01:57:36
发一些奇奇怪怪的联系方式或者邮箱

Yukio 01:57:55
给我发些什么监察委员会的邮箱

Yukio 01:58:32
我可以增加一个取消订阅按钮 让这些人取消订阅 别找我麻烦

Yukio 02:01:28
或者我把文件上传到一次性的文件分享页面

Yukio 02:01:38
过几个小时自动取消分享

## 随想 6

Yukio 01:06:16
这个我直播间可以根据uid和活跃等级

Yukio 01:06:24
持久化你的活跃度

Yukio 01:06:34
充钱也可以升级

Yukio 01:06:44
送我礼物

Yukio 01:07:21
如果是直接wx转钱给我 这个估计得给我发交易单号 私信发我才能兑换呢

Yukio 01:07:31
至于怎么找这个交易单号

Yukio 01:07:34
emm

Yukio 01:08:36
我想想

Yukio 01:09:28
这个估计得对接第四方交易接口 或者我看看现成的实现

Yukio 01:10:32
同时 给我的视频留言 发弹幕也可以刷活跃度

Yukio 01:10:42
刷直播间给你显示的活跃度

Yukio 01:12:39
如果给我充钱 我会发你涩图 冲的多发的多

Yukio 01:12:50
至于怎么发

Yukio 01:12:59
发你邮箱 你留下邮箱地址我发你

Yukio 01:15:57
不需要涩图也可以个性化定制

Yukio 01:16:19
如果给我充钱 一段时间内不会有给我打钱的二维码

Yukio 01:16:40
不给我充 不给我私信 我就一直发给我打钱的二维码

Yukio 01:17:37
如果给我充钱 可以绑定相关QQ账号 邮箱账号 或者什么其他的社交账号 每个平台只能绑一个账号

Yukio 01:18:14
绑了之后 给钱 一段时间我的内容没有打钱二维码 私信的话

你主动加我为好友才行

## 随想 5

Yukio 23:05:52
为了检测这种二维码

Yukio 23:06:30
同时有一些不是很好检测的文字 水印

Yukio 23:06:44
也需要image local contrast enhancement

Yukio 23:25:11
随机切割句子 分批发送

Yukio 23:25:16
这样我的机器人更像人

image enhancement for optical character recognition

image enhancement for watermark removal

## 随想 4

Yukio 21:00:32
nsfw没必要每一帧都加

Yukio 21:00:38
可以跳着加

Yukio 21:00:52
然后把出问题的帧的周围全部ban掉

Yukio 21:01:07
但是除了画面

Yukio 21:01:16
声音娇喘的也得去掉

Yukio 21:01:24
这个娇喘

Yukio 21:01:41
用个声音分类器

Yukio 21:01:51
用狗叫分类器改一下就好了

Yukio 21:02:12
除了娇喘

Yukio 21:02:20
还得弄语音识别

Yukio 21:02:35
防止某些狗叫言论污染直播间

## 随想 3

直播的通知 当直播的主题变化的时候 把广告发到不同的群 不同的观众那里

## 随想 2

不和谐的 包括有链接的内容 有二维码的内容 有联系方式的内容  加标点符号的广告内容 重复发送的内容

Yukio 14:26:10
可以看到其实判别不和谐言论很难

Yukio 14:26:23
所以可以用谐音字 拼音判断

Yukio 14:26:51
加上不信任期 一旦出现不和谐言论 一段时间内不用这个群聊

Yukio 14:27:15
以及繁体字转简体字

## 随想 1


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
