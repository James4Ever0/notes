---
tags: [API, soul]
title: Soul API
created: '2022-07-08T15:57:27.000Z'
modified: '2022-08-18T16:11:28.205Z'
---

# Soul APIs

灵魂测试卡片信息，获取签名*
https://api.soulapp.cn/html/measureResult/info/v2?userIdEcpt=加密用户ID

用户头像和签名等信息*
https://api-h5.soulapp.cn/html/v2/user/info?userIdEcpt=加密用户ID

单条瞬间展开信息*
https://api-h5.soulapp.cn/html/v3/post/detail?postIdEcpt=加密瞬间ID

单条瞬间展开页面*
https://w3.soulapp-inc.cn/activity/#/web/topic/detail?postIdEcpt=加密瞬间ID

用户发布瞬间信息，只有最新的10条*
https://api-h5.soulapp.cn/html/v2/post/homepage?userIdEcpt=加密用户ID

用户发布瞬间页面，只有最新的10条*
https://w3.soulapp-inc.cn/activity/#/web/user?userIdEcpt=加密用户ID

获取热门瞬间，只有最新的30条*
https://api-h5.soulapp.cn/html/v2/post/hot?pageIndex=1（前3页）

获取标签的瞬间信息，只有最新的30条*
https://api-h5.soulapp.cn/html/v2/tag/post?tagIdEcpt=加密标签ID

获取标签的瞬间页面，只有最新的30条*
https://w3.soulapp-inc.cn/activity/#/web/tag?tagIdEcpt=加密标签ID

随机播放音频信息，随机几首*
https://api-h5.soulapp.cn/html/v2/post/orimusicList/recommend

设置超萌捏脸页面*
https://app.soulapp.cn/avator/#/avatar/create?sex=1&version=3.10.0

注销账号页面*
https://app.soulapp.cn/app/#/account
https://app.soulapp.cn/app/#/destroy
