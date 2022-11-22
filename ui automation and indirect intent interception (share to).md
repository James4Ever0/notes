---
tags: [information gathering, scraping, stub, taobao, video]
title: ui automation and indirect intent interception (share to)
created: 2022-05-05T09:19:10+00:00
modified: 2022-11-22T12:02:48+08:00
---

淘宝视频 哇偶视频似乎取消了视频上方的搜索接口

首页的视频推荐似乎更好看一些 推荐算法更先进

逛逛被单独分了一个专栏 在那里可以搜索视频

## ui automation and indirect intent interception (share to)

"您的分享过于频繁，请稍后重试"

出现这种情况需要更换qq号

how about let's use appium for unlocking phone, airtest for actual testing?

appium can only unlock phone by removing password.

password with ampersand needs to be quoted/escaped.

that might need another supervisor

### appium

[write a test in python](https://appium.github.io/appium/docs/en/2.0/quickstart/test-py/)

[appium desired capabilities](http://appium.io/docs/en/writing-running-appium/caps/index.html#uiautomator2)

[uiautomator2](https://github.com/appium/appium-uiautomator2-driver)

[unlock android phone](https://github.com/appium/appium-android-driver/blob/master/docs/UNLOCK.md)

### airtest

[intro](https://airtest.doc.io.netease.com/en/tutorial/1_quick_start_guide/)

[poco introduction](https://airtest.doc.io.netease.com/en/tutorial/3_Poco_introduction/)

## autojs autox.js

[autojs code collection](https://blog.csdn.net/snailuncle2/article/details/115278704)

set up accessibility servicr for autox either by the switch inside settings (with root) or run this command:

```bash
adb shell settings put secure enabled_accessibility_services packagname/servicename
```

```bash
am start -n org.autojs.autoxjs.v6/org.autojs.autojs.external.shortcut.ShortcutActivity -a android.intent.action.MAIN -e path "/storage/emulated/0/脚本/show_toast.js"
```

现在autojs是付费的 但这两个都不能替代appium或者airtest

autox [repo](https://github.com/kkevsekk1/AutoX/tree/84a1f59135433f40747d18ac0805f1b4682bd032) [vscode plugin](https://github.com/kkevsekk1/Auto.js-VSCode-Extension)

[发送意图-QQ文本消息分享](https://github.com/feifadaima/https-github.com-hyb1996-NoRootScriptDroid/blob/eb4fff77db555ba391aeb39c61d3334f33be38d7/app/src/main/assets/sample/%E5%BA%94%E7%94%A8/%E5%8F%91%E9%80%81%E6%84%8F%E5%9B%BE-QQ%E6%96%87%E6%9C%AC%E6%B6%88%E6%81%AF%E5%88%86%E4%BA%AB.js)

[腾讯相关autojs](https://github.com/zmjjcghome/myAutoX/commit/f98c239ac3051fbd2a87d5913cf42125b9380af6#diff-905b728531cb73538660fa67cdc67dcc170d2e7cc9e7b73ba9b23eb3162aed53)


### frida

[hook current application context](https://github.com/frida/frida-java-bridge/issues/67)

### xposed

[xposed new repo](https://github.com/orgs/Xposed-Modules-Repo/repositories)

[android virtual cam](https://github.com/w2016561536/android_virtual_cam) xposed安卓虚拟摄像头 android virtual camera on xposed hook

#### broadcast, indirect intent, start activity

[highly suspected source of 'token', the miniapp json generator](https://github.com/tsuzcx/qq_apk/blob/dfa4bbb676ea1d1dc583317281980df86420ecb4/com.tencent.mobileqq/classes.jar/com/tencent/mobileqq/mini/share/MiniProgramOpenSdkUtil.java) the `MiniArkShareModelBuilder` `transformArkShareJson` `ShareQQArkHelper` `MiniProgramShareUtils` `MiniProgramShareUtils.newShareInfoRequest` `ShareManager` `MiniProgramShareUtils.shareToChatDirectly`

[qq jumpparser](https://github.com/waterwitness/qooq/blob/e723920ac555e99d5325b1d4024552383713c28d/classes2/com/tencent/mobileqq/utils/JumpParser.java)

[mqqapi doc](https://open.mobile.qq.com/api/mqq/index)

[mqqapi example](https://github.com/Kingcool759/Mydemo/blob/193b3807bcd309f28e45f03351f4d396e0ff726d/app/src/main/java/com/example/mydemo/blog/Case57.java)

[mqqapi 聊天 加群 名片](https://github.com/testacount1/HL4A/blob/fc2bd4289321fec27462aac2ac918d6b91646fe7/%E5%AE%89%E5%8D%93/src/main/java/%E6%94%BE%E8%AF%BE%E5%90%8E%E4%B9%90%E5%9B%AD%E9%83%A8/%E5%AE%89%E5%8D%93/%E5%B7%A5%E5%85%B7/%E9%93%BE%E6%8E%A5%E5%B7%A5%E5%85%B7.java)

[Android常用代码-微信QQ分享文件和文字](https://github.com/zhouzhuo810/BlogBackup/blob/98542d8f153012d38c0dff1d905a777f364566a7/source/_posts/Android%E5%B8%B8%E7%94%A8%E4%BB%A3%E7%A0%81-%E5%BE%AE%E4%BF%A1QQ%E5%88%86%E4%BA%AB%E6%96%87%E4%BB%B6%E5%92%8C%E6%96%87%E5%AD%97.md)

[常用的URL Scheme](https://www.jianshu.com/p/85aeae988443)

[Android am help 帮助信息](http://www.atmcu.com/277.html)

[adb shell am start -d 启动应用之uri被*吃了](https://blog.csdn.net/jack123lian/article/details/78796250)

[am start 启动activity 命令](https://www.jianshu.com/p/ab4bb360df36)

[inspeckage](https://github.com/ac-pm/Inspeckage) Android Package Inspector - dynamic analysis with api hooks, start unexported activities and more. (Xposed Module)

[找出APP的SchemeURL（抓取APP意图/intent）的常用方法](https://segmentfault.com/a/1190000040065334)

[隐式启动](https://www.coolapk.com/apk/xyz.hanks.launchactivity)  这是一款开发者辅助工具，帮助开发者发现手机上的应用的快捷启动，原理是利用 Android 提供的隐式启动 Activity 来快速启动某个应用的某个界面，如快速发微博、发朋友圈、扫一扫，快速切换 vpn 等

[adb/安卓/按键精灵/autojs/uniapp/ec打开SchemeURL的方法及常用SchemeURL整理](https://segmentfault.com/a/1190000040065447)

[Intent 拦截者_1.1.apk](https://474b.com/file/18365508-385607560)

[com.zwk.xintent](https://github.com/Xposed-Modules-Repo/com.zwk.xintent/releases) (intent traffic monitoring tool) release [orginal repo](https://github.com/2Y2s1mple/xintent)

use `am broadcast` to send indirect intent

[sending a boot-complete broadcast](https://riptutorial.com/android/example/18033/generating-a--boot-complete--broadcast)

[exploiting broadcast receivers](https://resources.infosecinstitute.com/topic/android-hacking-security-part-3-exploiting-broadcast-receivers/)

[usage of am](https://blog.csdn.net/yelangjueqi/article/details/43231425) and common android shell commands

## 腾讯微视

https://h5.weishi.qq.com/webapp/json/weishi/WSH5GetPlayPage?t=0.7532600494918984&g_tk=&feedid=71yYpleeM1HghTttk&recommendtype=0&datalvl=&qua=&uin=&format=json&inCharset=utf-8&outCharset=utf-8

## 淘宝短视频

[淘宝x-sign算法分析](https://blog.csdn.net/tiandaochouqin_W/article/details/118225639?spm=1001.2101.3001.6650.1&utm_medium=distribute.wap_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-1-118225639-blog-115668447.wap_blog_relevant_default&depth_1-utm_source=distribute.wap_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-1-118225639-blog-115668447.wap_blog_relevant_default)

[淘宝抓包解决方案](https://blog.csdn.net/junges/article/details/103036012?spm=1001.2101.3001.6650.4&utm_medium=distribute.wap_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-4-103036012-blog-115668447.wap_blog_relevant_default&depth_1-utm_source=distribute.wap_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-4-103036012-blog-115668447.wap_blog_relevant_default)

[逆向闲鱼apk 抓包](https://www.52pojie.cn/forum.php?mod=viewthread&tid=1582470)

post content on we.taobao.com

淘宝直播

https://zhuanlan.zhihu.com/p/91192587

packet capture + batch m3u8 download 

5 666:/鱼里家庭布偶猫舍的场间简直太火爆了，快来看！
可爱的宝宝找家咯 ,快来场间  https://m.tb.cn/h.fJErCBC?sm=b4d048

———————口———————
！们那之学有为上家得人多啊

淘宝网页无法播放直播

http://huodong.m.taobao.com/act/talent/live.html?id=359158835379&type=508&livesource=share&cp_origin=taobaozhibo%7Ca2141.8001249%7C%7B%22account_id%22%3A%221897661676%22%2C%22app_key%22%3A%2221646297%22%2C%22feed_id%22%3A%22359158835379%22%2C%22os%22%3A%22android%22%2C%22spm-cnt%22%3A%22a2141.8001249%22%7D&sourceType=talent&suid=07ebc365-efc6-4e9c-9c14-c58c1bb8e522&ut_sk=1.W4yy2CtIMUMDAA1l3Dnx4jNG_21646297_1651743901078.Copy.zhibo&un=42ad1253bebcb796f3ba5a7177d3a823&share_crt_v=1&un_site=0&spm=a2159r.13376460.0.0&sp_abtk=common_zhibo_commonInfo&sp_tk=5Lus6YKj5LmL5a2m5pyJ5Li65LiK5a625b6X5Lq65aSa&cpp=1&shareurl=true&short_name=h.fJErCBC&bxsign=scdS6H1ZsIpmAMTuhs-TbALYgOScV_BU6U9ueNABqjzLXd9JSLZYxA6vuaR_tN9PI3n6qDUMtmf-5O_pZZqgnoLHg4WsX64s_Gkx--xc0vfG_87x3Boc1-uCbsYXCZO3Wtc

最新版只有微淘入口

淘宝逛逛 有用户名 ID

67信生对在然有为上子是去你嘻 https://m.tb.cn/h.fJE9C6B?sm=ee59f9  怕鱼的小猫咪~~

this video is flipable

淘宝网页版

https://main.m.taobao.com/index.html

https://market.m.taobao.com/app/tb-source-app/video-fullpage/pages/index?wh_weex=true&wx_navbar_hidden=true&contentId=346882467812&source=guess-guangguang&type=guangguang_cainixihuan&id=346882467812

https://market.m.taobao.com/app/tb-source-app/video-fullpage/pages/index?wh_weex=true&wx_navbar_hidden=true&origin=VideoInteract%7Ca310p.13800399.0.0%7C%7B"contentId"%3A"346882467812"%7D&contentId=346882467812&source=guess-guangguang&type=guangguang_cainixihuan&spm=a2141.1.guessitemtab_1.3&accountId=0&videoUrl=https%3A%2F%2Fcloud.video.taobao.com%2Fplay%2Fu%2Fnull%2Fp%2F1%2Fe%2F6%2Ft%2F1%2F346882467812.mp4&coverImage=https%3A%2F%2Fimg.alicdn.com%2Fimgextra%2Fi2%2F604321789%2FO1CN01rVTgs31P5PIQ7r2JR_!!604321789.jpg&id=346882467812&sourceType=other&suid=7f31e56f-2878-4462-9a5a-acd7d5deeec5&ut_sk=1.W4yy2CtIMUMDAA1l3Dnx4jNG_21646297_1651742283972.Copy.tblive-video&un=42ad1253bebcb796f3ba5a7177d3a823&share_crt_v=1&un_site=0&sp_abtk=common_tblive-video_commonInfo&sp_tk=55Sf5a%2B55Zyo54S25pyJ5Li65LiK5a2Q5piv5Y675L2g&cpp=1&shareurl=true&short_name=h.fJE9C6B&bxsign=scdwHO4PyMrtSLzA7OBHe89rxDFffyg-UVrE4mtFb42ts8qjhHx_6DhU0VAdOy3PgJcoggVVt1dw63IPVDTdXhIGiWlqtdNZredQE5O2V8o1AhV8XE7zhYjf5gApjy90rf1&sm=ee59f9&app=chrome
