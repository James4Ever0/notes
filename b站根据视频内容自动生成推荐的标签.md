---
title: b站根据视频内容自动生成推荐的标签
created: '2022-10-25T06:16:01.000Z'
modified: '2022-11-04T07:16:55.519Z'
---

# b站根据视频内容自动生成推荐的标签

B站允许最多10个标签

不能发布太频繁, B站官方限制**30秒一稿**

[some upload api](https://github.com/xunsword/bilibil/blob/2abf66a9771daebc12c181f88d8af82613975548/bilibili_up.py)

this api does not analyze the video content. it only predict tags from metadata:

`https://member.bilibili.com/x/web/archive/tags`

[how to get upload_id](https://github.com/xunsword/bilibil/blob/2abf66a9771daebc12c181f88d8af82613975548/bilibili_up.py)

只有PC网页端有这个 手机端没有 可能是新功能

b站最新更新了这两个接口 需要传入upload_id 具体参数抓包获取

分区推荐 POST：
https://member.bilibili.com/x/vupre/web/archive/types/predict

标签推荐 GET（可能有延迟 需要请求两次 因为第一次标签数量较少）：
https://member.bilibili.com/x/vupre/web/tag/recommend

获取活动标签:
https://member.bilibili.com/x/vupre/web/topic/type?type_id=21&pn=0&ps=200&title=20210210_298667075925_waou_5s&t=1667530591393
