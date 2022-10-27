---
title: mitmchat
created: 2022-10-14T11:09:39+00:00
modified: 2022-10-27T13:22:44+08:00
---

# mitmchat

## 计算句子相关度 计算下一句话的可能性 predict next sentence probability

[bing search entries](https://cn.bing.com/search?q=predict+next+sentence+probability&form=QBLH&sp=-1&pq=predict+next+sentence+probabilit&sc=8-32&qs=n&sk=&cvid=7BFC0E30DD634E3EAD7B0A769634C98C&ghsh=0&ghacc=0&ghpl=)

[next sentence prediction using bert](https://www.geeksforgeeks.org/next-sentence-prediction-using-bert/)

[github topic next semtence prediction](https://github.com/topics/next-sentence-prediction)

## grammar checker, sentence corrector

[languagetool](https://languagetool.org) rule based grammar error checker [repo](https://github.com/languagetool-org/languagetool)

## chatterbot retrain issue

train chatterbot with the recent knowledge

sql schema:

| end_of_list | content |
|-------------|---------|
|  false      |  some text content    |
|  false      |  some text content    |
|  true       |    2022-01-03 |

## additional notices, about delivery efficiency

正在刷屏的群里面也不能发消息 不能确保对象是否收到消息

Yukio 12:46:35
今天mitm有个问题

Yukio 12:46:43
mitm的两个人

Yukio 12:46:48
都不能屏蔽我

Yukio 12:46:53
不然mitm失效

Yukio 12:47:22
但是我现在不知道这个怎么看别人屏蔽我没有

Yukio 12:47:28
可能以后就知道了

Yukio 12:49:17
我可以获取群禁言情况


## mitmchat with video and text how to get embedding?

Yukio 18:40:25
mitmchat的定义

Yukio 18:41:31
在同一个时间段内 把正在讨论相同话题 但是不认识的两个人 互相传话一段时间并断开

Yukio 18:42:28
多个mitmchat的定义

Yukio 18:43:26
多个mitm的话 所有被mitm的对象

Yukio 18:43:33
都不能相互认识

Yukio 18:43:56
也就是两两不认识 两两不在同一个群里面

Yukio 18:44:40
delayed mitmchat

Yukio 18:45:08
也就是a和b不在同一个时间段内

Yukio 18:45:22
根据b现在的内容

Yukio 18:45:29
回复a之前的内容

Yukio 18:47:46
所有的mitmchat

Yukio 18:47:57
前提都是a和b互相不认识

Yukio 18:49:01
也不能是它自己

Yukio 18:55:51
所以分为两种

Yukio 18:56:00
mitmchat

Yukio 18:56:12
instant mitm和delayed mitm

Yukio 18:56:37
delayed就是话传不回去

Yukio 18:57:10
只能传回机器人 机器人没有反馈机制那么就不会像人

Yukio 19:08:40
像这种图片 怎么个embedding 图片要能做clip才行

Yukio 19:13:06
起止时间确定

Yukio 19:15:01
如果不能本地部署clip模型 也得利用图片反向搜索 获得图片的关键词才行

Yukio 19:16:18
图片反查 然后bm25 textrank

Yukio 19:16:34
获得是否在讨论相同话题的判断
