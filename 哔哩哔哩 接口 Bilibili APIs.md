---
tags: [API, bilibili, stub]
title: 哔哩哔哩 接口 Bilibili APIs
created: '2022-07-09T15:30:05.000Z'
modified: '2024-03-29T14:59:23.338Z'
---

# 哔哩哔哩 接口 Bilibili APIs

哔哩哔哩对user agent有校验 要使用浏览器的UA或者fake_useragent的UA

生成随机的`dm_*`参数

```python
{
    "dm_img_list": "[]",  # 鼠标/键盘操作记录
    "dm_img_str": "".join(random.sample(dm_rand, 2)),
    "dm_cover_img_str": "".join(random.sample(dm_rand, 2)),
    "dm_img_inter": '{"ds":[],"wh":[0,0,0],"of":[0,0,0]}',
}
```

合成`wbi`校验数据的算法没有变化

----

[bilibili上传工具 biliup](https://github.com/biliup/biliup)

[bilibili toolkit](https://github.com/Hsury/Bilibili-Toolkit)

api合集
https://www.bilibili.com/read/cv3430609/

官方接口文档
https://github.com/fython/BilibiliAPIDocs

直播api
https://github.com/lovelyyoshino/Bilibili-Live-API

野生api收集
https://github.com/SocialSisterYi/bilibili-API-collect

python api
https://github.com/MoyuScript/bilibili-api
https://github.com/Nemo2011/bilibili-api (current)
https://github.com/Vespa314/bilibili-api

[提交视频剧情树](https://nemo2011.github.io/bilibili-api/#/examples/interactive_video)
