---
tags: [browser extension, cloud sync, extension, image sources, information gathering, search engine, sync, text sources, video sources]
title: Netdisk managers, Userscript and info_data collection
created: 2022-04-25T20:54:07+00:00
modified: 2023-01-30T04:50:36+08:00
---

# Userscript and info/data collection

[Alist](https://github.com/alist-org/alist) a filelist manager for all common cloud storage providers

for site collection list you could just search for it.

you can search for netdisk managers.

aliyun netdisk manager:
https://github.com/tickstep/aliyunpan

found a repo full of userscripts:
https://github.com/XIU2/UserScript

baidunetdisk cli go:
https://github.com/qjfoidnh/BaiduPCS-Go

bittorrent trackers:
https://github.com/XIU2/TrackersListCollection

script list:
护眼模式 	简单有效的全网通用护眼模式、夜间模式、暗黑模式~ 	安装 | 备用
	知乎 美化 	宽屏显示、暗黑模式、屏蔽首页活动、调整图片最大高度... 	安装 | 备用
	知乎 增强 	移除登录弹窗、屏蔽首页视频、屏蔽用户、屏蔽关键词... 	安装 | 备用
	V2EX 增强 	自动签到、链接转图片、自动无缝翻页、新标签页打开链... 	安装 | 备用
	Github 增强 	高速下载 Git Clone/SSH、Release、Raw、Code(ZIP) ... 	安装 | 备用
	Ping.Sx 增强 	一键复制所有 IP、清理 IP 链接、快捷回到顶部 ... 	安装 | 备用
	自动无缝翻页 * 	无缝衔接下一页内容 (瀑布流) 支持各论坛/漫画/百度/谷歌等... 	安装 | 备用
	3DM论坛 美化 	精简多余内容、样式优化 	安装 | 备用
	3DM论坛 增强 	自动回复、自动无缝翻页、清理置顶帖子、自动滚至隐藏... 	安装 | 备用
	蓝奏云网盘 增强 * 	右键显示菜单、直接下载文件、显示更多文件、自动密码... 	安装 | 备用
	新标签页打开链接 * 	将网页中所有链接改为新标签页打开~ 	安装 | 备用
	DuckDuckGo 增强 	屏蔽指定域名、修复图标加载、链接不携来源、快捷回到... 	安装 | 备用
	吾爱破解论坛 美化 	精简多余内容、样式优化 	安装 | 备用
	吾爱破解论坛 增强 	自动签到、自动无缝翻页、屏蔽导读悬赏贴 (最新发表页)... 	安装 | 备用
	全球主机交流论坛 增强 * 	自动访问空间(22积分)、屏蔽用户、屏蔽关键词、自动翻... 	安装 | 备用
	Steam 创意工坊大图 修复 	修复 Steam 创意工坊预览大图无法显示的问题 	安装 | 备用
	HTML5 视频音频默认音量 	避免被 100% 音量吓一跳！且支持各网站分别记住音量... 	安装 | 备用
	Google 翻译 美化 	精简多余内容、修复翻译结果溢出屏幕问题 	安装 | 备用
	智友邦论坛 美化 	精简多余内容、样式优化、宽屏显示 	安装 | 备用
	智友邦论坛 增强 	自动签到、自动回复、自动无缝翻页、快捷回到顶部、附... 	安装 | 备用

autopager:
https://greasyfork.org/en/scripts/419215-%E8%87%AA%E5%8A%A8%E6%97%A0%E7%BC%9D%E7%BF%BB%E9%A1%B5

autopager supported websites:
< - - - - - - - - 网站 - - - - - - - - > 	主页 	分类 	文章 	评论 	搜索 	< - - - - - - - - - - - - - - - - - - - - - - - - - 备注 - - - - - - - - - - - - - - - - - - - - - - - - - >
所有 Discuz! 论坛 	✔ 	✔ 	✔ 	- 	✔ 	国内常见 论坛系统 (如：吾爱破解、3DM 等)
所有 phpBB 论坛 	✔ 	✔ 	✔ 	- 	✔ 	国外常见 论坛系统
所有 XenForo 论坛 	✔ 	✔ 	✔ 	- 	✔ 	国外常见 论坛系统
所有 NexusPHP 论坛 	✔ 	✔ 	✔ 	- 	✔ 	国内常见 论坛系统 (BT / PT 论坛)
所有 Flarum 论坛 	✔ 	✔ 	✔ 	- 	✔ 	简洁开源 论坛系统
所有 Xiuno 论坛 	✔ 	✔ 	✔ 	- 	✔ 	国内开源 论坛系统
所有 笔趣阁 网站 	- 	- 	✔ 	- 	- 	小说网站常用的 笔趣阁 模板
部分 Typecho 网站 	✔ 	✔ 	- 	- 	✔ 	适配一些常见的 Typecho 网站主题
部分 WordPress 网站 	✔ 	✔ 	- 	- 	✔ 	适配一些常见的 WordPress 网站主题
部分 在线影视模板 网站 	✔ 	✔ 	- 	- 	✔ 	适配一些常见的 在线影视 网站模板
部分 自带无缝翻页 网站 	✔ 	✔ 	- 	- 	✔ 	适配一些支持 [加载更多] 的网站 (为了避免误触，规则比较保守)
						> [搜索引擎] <
谷歌 (Google) 	- 	- 	- 	- 	✔ 	(建议开启各搜索引擎设置中的 新标签页打开链接 选项，以提高使用体验)
必应 (Bing) 	- 	- 	- 	- 	✔ 	(微软的)
百度 	- 	- 	- 	- 	✔ 	
搜狗 	- 	- 	- 	- 	✔ 	
搜狗微信 	✔ 	✔ 	- 	- 	✔ 	(微信文章/公众号搜索)
头条搜索 	- 	- 	- 	- 	✔ 	
神马搜索 	- 	- 	- 	- 	✔ 	
无追搜索 	- 	- 	- 	- 	✔ 	
360 搜索 	- 	- 	- 	- 	✔ 	
Searxng 	- 	- 	- 	- 	✔ 	(对各大搜索引擎的聚合搜索)
DuckDuckGo 	- 	- 	- 	- 	✔ 	(以上这几个均支持手机版)
Startpage 	- 	- 	- 	- 	✔ 	
Yandex 	- 	- 	- 	- 	✔ 	(俄罗斯的，如果卡住说明弹验证码了，请刷新网页后继续...)
Yahoo 	- 	- 	- 	- 	✔ 	(包含 Yahoo JP 域名)
Qwant 	- 	- 	- 	- 	✔ 	
Ecosia 	- 	- 	- 	- 	✔ 	
Goobe 	- 	- 	- 	- 	✔ 	(代码相关)
Magi 	- 	- 	- 	- 	✔ 	
轻搜 	- 	- 	- 	- 	✔ 	
ASK 	- 	- 	- 	- 	✔ 	
						> [社区] <
贴吧 	- 	✔ 	✔ 	- 	✔ 	(如要发帖请点击右侧悬浮 [发帖] 按钮 或 点击左下角页码暂停翻页)
豆瓣 	- 	✔ 	✔ 	✔ 	- 	(短评、影评、评论、小组帖子 等等...)
知乎 	- 	✔ 	- 	- 	- 	(用户主页下的回答、文章 与 收藏夹页)
微博 	- 	- 	- 	✔ 	- 	
天涯 	- 	✔ 	✔ 	- 	- 	
虎扑 	- 	✔ 	✔ 	- 	- 	
NGA 	- 	✔ 	✔ 	- 	- 	(玩家相关)
V2EX 	✔ 	✔ 	- 	- 	- 	
煎蛋网 	✔ 	✔ 	- 	✔ 	- 	
水木社区 	- 	✔ 	✔ 	- 	- 	(清华论坛)
龙的天空 	- 	✔ 	✔ 	- 	- 	(小说相关)
看雪论坛 	- 	✔ 	- 	- 	- 	(安全相关)
番组计划 (Bangumi) 	- 	✔ 	- 	- 	- 	(二次元版豆瓣？)
懂车帝论坛 	- 	✔ 	- 	- 	- 	
宽带山论坛 	✔ 	✔ 	✔ 	- 	- 	(上海地方论坛)
篱笆网论坛 	✔ 	✔ 	✔ 	- 	✔ 	(上海地方论坛)
淘股吧论坛 	✔ 	✔ 	✔ 	- 	- 	
芥子空间论坛 	- 	✔ 	- 	- 	- 	(手游相关)
LowEndTalk 	✔ 	✔ 	✔ 	- 	- 	(海外服务器相关)
RuTracker 	- 	✔ 	✔ 	- 	- 	(俄罗斯学习资源论坛)
A 岛 	- 	✔ 	✔ 	- 	- 	
B 站 (Bilibili) 	- 	- 	- 	- 	✔ 	
						> [设计/素材] <
Pixiv 	- 	✔ 	- 	- 	✔ 	(插画)
Vilipix 	- 	✔ 	- 	- 	✔ 	(内容来自 Pixiv，下同 ⤵)
Pixivision 	- 	✔ 	- 	- 	✔ 	
站酷 (ZCOOL) 	✔ 	- 	- 	- 	- 	(图片/设计素材，下同 ⤵)
千图网 	- 	✔ 	- 	- 	✔ 	
千库网 	- 	✔ 	- 	- 	✔ 	
昵图网 	- 	✔ 	- 	- 	✔ 	
众图网 	- 	✔ 	- 	- 	✔ 	
我图网 	- 	✔ 	- 	- 	✔ 	
包图网 	- 	✔ 	- 	- 	✔ 	
图怪兽 	- 	✔ 	- 	- 	✔ 	
Pixabay 	- 	✔ 	- 	- 	✔ 	
搜图神器 	✔ 	- 	- 	- 	✔ 	
素材中国 	- 	✔ 	- 	- 	✔ 	
iconfont 	- 	- 	- 	- 	✔ 	(图标，下同 ⤵)
IconArchive 	- 	- 	- 	- 	✔ 	
Mixkit 	- 	✔ 	- 	- 	✔ 	(视频/音乐素材)
普象网 	✔ 	✔ 	- 	- 	✔ 	(产品设计，下同 ⤵)
学犀牛 	✔ 	✔ 	✔ 	- 	✔ 	
欧模网 	- 	✔ 	- 	- 	✔ 	(模型素材，下同 ⤵)
下得乐 	- 	✔ 	- 	- 	✔ 	
						> [游戏] <
3DM 	- 	✔ 	✔ 	- 	- 	(包括论坛，下同 ⤵)
游侠网 	- 	✔ 	✔ 	- 	- 	
游民星空 	- 	- 	✔ 	- 	- 	
3DM MOD 	- 	✔ 	- 	- 	✔ 	(游戏 MOD，下同 ⤵)
CurseForge 	- 	✔ 	- 	- 	✔ 	
NexusMods 	- 	✔ 	- 	- 	✔ 	
Steam 创意工坊 	✔ 	✔ 	- 	- 	✔ 	(创意工坊 MOD 文件下载1/下载2)
Steam 活动评论 	- 	- 	- 	✔ 	- 	(商家动态/活动下的评论区)
小霸王其乐无穷 	✔ 	✔ 	- 	- 	✔ 	
Switch520 	✔ 	✔ 	- 	- 	✔ 	
CS.RIN.RU 	- 	✔ 	✔ 	- 	✔ 	(国外的游戏分享网站，下同 ⤵)
Byrutor 	✔ 	✔ 	- 	- 	- 	
Crackhub213 	✔ 	✔ 	- 	- 	✔ 	
FitGirl Repacks 	✔ 	✔ 	- 	- 	✔ 	
Masquerade Repacks 	✔ 	✔ 	- 	- 	✔ 	
						> [影视/在线] <
茶杯狐 	- 	- 	✔ 	- 	✔ 	(以下部分网站同时包含 BT/动漫)
NO 视频 	- 	✔ 	- 	- 	✔ 	
低端影视 	✔ 	✔ 	- 	- 	✔ 	
奈菲影视 	- 	✔ 	- 	- 	✔ 	
在线之家 	- 	✔ 	- 	- 	✔ 	
片吧影院 	- 	✔ 	- 	- 	✔ 	
嗯哩嗯哩 	- 	✔ 	- 	- 	✔ 	
91 美剧网 	- 	✔ 	- 	- 	✔ 	
真不卡影院 	- 	✔ 	- 	- 	✔ 	
ZzzFun 动漫 	- 	✔ 	- 	- 	✔ 	(仅动漫，下同 ⤵)
吐槽弹幕网 	- 	✔ 	- 	- 	✔ 	
樱花动漫 	- 	✔ 	- 	- 	✔ 	
怡萱动漫 	- 	✔ 	- 	- 	✔ 	
妮可动漫 	- 	✔ 	- 	- 	✔ 	
漫岛动漫 	- 	✔ 	- 	- 	✔ 	
AGE 动漫 	- 	✔ 	- 	- 	✔ 	
233 动漫 	- 	✔ 	- 	- 	✔ 	
Anime1 	✔ 	- 	- 	- 	✔ 	
						> [BT/下载] <
音范丝 	✔ 	✔ 	- 	- 	✔ 	
片源网 	- 	- 	- 	- 	✔ 	
磁力狗 	- 	- 	- 	- 	✔ 	
雨花阁 	- 	- 	- 	- 	✔ 	
BT 之家 	✔ 	✔ 	- 	- 	✔ 	(匹配所有包含 btbtt 的域名)
BD 影视 	- 	✔ 	- 	- 	✔ 	
高清电台 	✔ 	✔ 	- 	- 	✔ 	
爱恋动漫 	✔ 	✔ 	- 	- 	✔ 	(动漫，下同 ⤵)
末日动漫 	✔ 	✔ 	- 	- 	✔ 	(包括 国际站)
动漫花园 	✔ 	✔ 	- 	- 	✔ 	(包括 镜像站)
简单动漫 	✔ 	✔ 	- 	- 	✔ 	
零度动漫 	✔ 	✔ 	- 	- 	✔ 	
ACG.RIP 	✔ 	✔ 	- 	- 	✔ 	
萌番组 	✔ 	✔ 	- 	- 	✔ 	(包括 Lite 版)
MioBT 	✔ 	✔ 	- 	- 	✔ 	
SkrBT 	✔ 	✔ 	- 	- 	✔ 	(匹配所有包含 skrbt 的域名)
Nyaa 	✔ 	- 	- 	- 	✔ 	
YTS 	- 	✔ 	- 	- 	✔ 	(这个 + 下面这两个算是我最常用的了~)
1337x 	✔ 	✔ 	- 	- 	✔ 	(包括 镜像站)
RARBG 	✔ 	✔ 	- 	- 	✔ 	(包括 镜像站)
Zooqle 	- 	✔ 	- 	- 	✔ 	
Kickass 	- 	✔ 	- 	- 	✔ 	
WebHD 	✔ 	- 	- 	- 	✔ 	(与 SubHD 字幕网站配套)
MINI4K 	- 	✔ 	- 	- 	✔ 	(与 A4k 字幕网站配套)
Trackerslist.com 	- 	- 	- 	- 	- 	(分享我自制自用的 Tracker 列表，多少会提高点 BT 下载速度~ 12k+⭐)
						> [字幕] <
A4k 	✔ 	✔ 	- 	- 	✔ 	
SubHD 	- 	✔ 	- 	- 	✔ 	
伪射手网 	- 	✔ 	- 	- 	✔ 	
点点字幕 	- 	- 	- 	- 	✔ 	
中文字幕网 	- 	✔ 	- 	- 	✔ 	
字幕库 	✔ 	✔ 	- 	- 	✔ 	
						> [漫画] <
漫本 	- 	✔ 	✔ 	- 	- 	
好漫 6 	- 	✔ 	✔ 	- 	✔ 	
6 漫画 	- 	✔ 	✔ 	- 	- 	
动漫狂 	- 	✔ 	✔ 	- 	✔ 	(部分早期章节，因网站问题而无法自动衔接下一章)
动漫啦 	- 	✔ 	✔ 	- 	✔ 	
漫漫聚 	- 	- 	✔ 	- 	- 	
漫画猫 	- 	✔ 	✔ 	- 	✔ 	
漫画皮 	- 	✔ 	✔ 	- 	- 	
漫画人 	- 	- 	✔ 	- 	- 	
漫画柜 	- 	✔ 	✔ 	- 	✔ 	
36漫画 	- 	✔ 	✔ 	- 	✔ 	
爱漫画 	- 	✔ 	✔ 	- 	✔ 	
漫画 DB 	- 	✔ 	✔ 	- 	✔ 	
HiComic (嗨漫画) 	- 	- 	✔ 	- 	- 	
动漫之家 (主站) 	- 	✔ 	✔ 	- 	✔ 	(这网站两个域名内容不一样 ⤵)
动漫之家 (日漫) 	- 	✔ 	✔ 	- 	✔ 	
阿狸漫画 	- 	✔ 	✔ 	- 	✔ 	
快岸漫画 	- 	✔ 	✔ 	- 	✔ 	
动漫之家 	- 	- 	✔ 	- 	- 	
动漫戏说 	- 	✔ 	✔ 	- 	- 	
优酷漫画 	- 	✔ 	✔ 	- 	✔ 	
拷贝漫画 	- 	✔ 	✔ 	- 	- 	
木马漫画 	- 	✔ 	✔ 	- 	- 	
漫画星球 	- 	✔ 	✔ 	- 	- 	
风之动漫 	- 	- 	✔ 	- 	- 	
包子漫画 	- 	- 	✔ 	- 	- 	
乐语漫画 	- 	✔ 	✔ 	- 	✔ 	
新新漫画 	- 	✔ 	✔ 	- 	✔ 	
188漫画网 	- 	- 	✔ 	- 	- 	
古风漫画网 	- 	✔ 	✔ 	- 	✔ 	
砂之船动漫家 	- 	✔ 	✔ 	- 	✔ 	
Mangabz 漫画 	- 	✔ 	✔ 	- 	✔ 	
Xmanhua 漫画 	- 	✔ 	✔ 	- 	✔ 	
COCOMANGA 漫画 	- 	✔ 	✔ 	- 	✔ 	
						> [小说] <
起点中文 	- 	✔ 	✔ 	- 	- 	
七猫中文 	- 	- 	✔ 	- 	- 	
知轩藏书 	- 	✔ 	- 	- 	- 	(仅下载)
宝书网 	- 	✔ 	- 	- 	- 	(仅下载)
御书网 	- 	✔ 	✔ 	- 	- 	
owLook 	- 	- 	✔ 	- 	- 	(支持在线阅读的小说搜索引擎)
铅笔小说 	- 	✔ 	✔ 	- 	- 	
无错小说网 	- 	✔ 	✔ 	- 	✔ 	
读书族小说网 	- 	- 	✔ 	- 	- 	
哔哩轻小说 	- 	✔ 	✔ 	- 	- 	(包括 手机版，轻小说，下同 ⤵)
话本小说网 	- 	- 	✔ 	- 	- 	
轻之文库 	- 	✔ 	✔ 	- 	✔ 	
Archive of OurOwn 	- 	✔ 	✔ 	- 	✔ 	
精品书源 	- 	- 	- 	- 	- 	(分享我自制自用的「阅读」APP 精品书源 1.6k+⭐)
						> [软件分享] <
蓝鲨 	✔ 	✔ 	- 	- 	✔ 	
不死鸟 	✔ 	✔ 	- 	- 	✔ 	
分享者 	✔ 	✔ 	- 	- 	✔ 	
扩展迷 	- 	✔ 	- 	- 	- 	(浏览器扩展)
MacWK 	- 	✔ 	- 	- 	✔ 	(MAC 相关)
小众软件 	✔ 	✔ 	- 	- 	✔ 	
乐软博客 	✔ 	✔ 	- 	- 	✔ 	
果核剥壳 	✔ 	✔ 	- 	- 	✔ 	
六音软件 	✔ 	✔ 	- 	- 	✔ 	
反斗软件 	✔ 	✔ 	- 	- 	✔ 	
微当下载 	✔ 	✔ 	- 	- 	✔ 	
大眼仔旭 	- 	✔ 	- 	- 	✔ 	
423Down 	✔ 	✔ 	- 	✔ 	✔ 	
发烧友绿软 	✔ 	✔ 	- 	- 	✔ 	
异次元软件 	✔ 	✔ 	- 	✔ 	✔ 	
悪魔の小站 	✔ 	✔ 	- 	- 	✔ 	
老殁殁漂遥 	✔ 	✔ 	- 	- 	✔ 	
腾龙工作室 	✔ 	✔ 	- 	- 	- 	
异星软件空间 	✔ 	✔ 	- 	- 	✔ 	
Nite07 的小窝 	✔ 	- 	- 	- 	- 	
Sordum 	✔ 	✔ 	- 	- 	✔ 	(国外的软件分享网站，下同 ⤵)
Winaero 	- 	✔ 	- 	- 	- 	
LRepacks 	✔ 	✔ 	- 	- 	- 	
DlAndroid 	- 	✔ 	- 	- 	✔ 	(国外安卓 App 相关)
Winhelponline 	✔ 	✔ 	- 	- 	- 	
WindowsLatest 	✔ 	✔ 	- 	- 	- 	
TheWindowsClub 	✔ 	✔ 	- 	- 	- 	
						> [学术] <
Wiley Online Library 	- 	- 	- 	- 	✔ 	
ACS (Publications) 	- 	- 	- 	- 	✔ 	
Library Genesis 	- 	- 	- 	- 	✔ 	(匹配所有包含 libgen 的域名)
ScienceDirect 	- 	- 	- 	- 	✔ 	
Z-Library 	- 	- 	- 	- 	✔ 	(包括 镜像站)
PubMed 	- 	- 	- 	- 	✔ 	
X-MOL 	- 	✔ 	- 	- 	✔ 	
维普网 	- 	- 	- 	- 	✔ 	
科研通 	- 	✔ 	✔ 	- 	✔ 	
酷科研 	- 	- 	✔ 	- 	- 	
小木虫 	- 	✔ 	✔ 	- 	✔ 	
百度学术 	- 	✔ 	- 	- 	✔ 	
必应学术 (Bing) 	- 	- 	- 	- 	✔ 	
谷歌学术 (Google) 	- 	- 	- 	- 	✔ 	包括 镜像站1 / 2
国家自然科学基金 	- 	- 	✔ 	- 	- 	
						> [编程/技术] <
StackOverflow 	- 	✔ 	- 	- 	✔ 	技术问答
SegmentFault 	- 	✔ 	- 	- 	✔ 	
W3Cschool 	- 	✔ 	- 	- 	- 	编程教程
W3school 	- 	✔ 	- 	- 	- 	
菜鸟教程 	- 	✔ 	- 	- 	- 	
博客园 	✔ 	✔ 	- 	- 	✔ 	技术博客
51CTO 	✔ 	✔ 	- 	- 	✔ 	
Gitee 	- 	✔ 	✔ 	✔ 	✔ 	开源分享
Github 	✔ 	✔ 	✔ 	✔ 	✔ 	(建议搭配我另一个 Github 增强 - 高速下载 油猴脚本~)
						> [资讯/科技] <
ScienceAlert 	✔ 	✔ 	- 	- 	- 	
果壳网 	✔ 	✔ 	- 	✔ 	- 	
蓝点网 	- 	✔ 	- 	- 	- 	
可能吧 	✔ 	✔ 	- 	- 	- 	
超能网 	✔ 	✔ 	- 	- 	- 	
IT之家 	- 	✔ 	- 	- 	- 	
36 氪 	- 	✔ 	- 	- 	- 	
						> [其他] <
IMDb 	- 	✔ 	- 	- 	✔ 	
烂番茄 	- 	✔ 	- 	- 	✔ 	
致美化 	- 	✔ 	- 	- 	- 	系统美化
蓝奏云 	- 	✔ 	- 	- 	- 	网盘 (后台及分享链接列表)
新片场 	- 	✔ 	- 	- 	- 	视频短片
wikiHow 	- 	✔ 	- 	- 	✔ 	指南
AfreecaTV 	✔ 	✔ 	- 	- 	- 	直播 (大都是韩国人)
GreasyFork 	✔ 	✔ 	- 	✔ 	✔ 	本站
UserScript 	- 	- 	- 	- 	✔ 	油猴脚本的聚合搜索 (Tampermonkey 作者做的)
UserStyles 	✔ 	✔ 	- 	✔ 	✔ 	
Quicker 	✔ 	✔ 	- 	✔ 	✔ 	
Xposed 	- 	✔ 	- 	- 	✔ 	
书签地球 	✔ 	- 	- 	- 	✔ 	
什么值得买 	- 	✔ 	- 	- 	✔ 	
没得比导购 	- 	✔ 	- 	- 	✔ 	
叽哩叽哩日报 	- 	✔ 	- 	- 	- 	
彼岸图网 	✔ 	✔ 	- 	- 	- 	壁纸 (下同 ⤵)
必应壁纸 	✔ 	✔ 	- 	- 	- 	
动漫壁纸 	- 	✔ 	- 	- 	✔ 	
动漫壁纸2 	- 	✔ 	- 	- 	✔ 	
HDQwalls 	✔ 	✔ 	- 	- 	✔ 	
Nastol 	✔ 	✔ 	- 	- 	✔ 	
以上仅为一小部分... 						持续添加中，欢迎申请~

potential useful websites:
https://greasyfork.org/en/users/sign_in?return_to=%2Fen%2Fsc…%25E6%2597%25A0%25E7%25BC%259D%25E7%25BF%25BB%25E9%25A1%25B5 debugger eval code:1:60
https://greasyfork.org/scripts/419215-%E8%87%AA%E5%8A%A8%E6%…8%87%AA%E5%8A%A8%E6%97%A0%E7%BC%9D%E7%BF%BB%E9%A1%B5.user.js debugger eval code:1:60
https://greasyfork.org/en/help/installing-user-scripts debugger eval code:1:60
https://greasyfork.org/scripts/419081-%E7%9F%A5%E4%B9%8E%E5%…E%E5%BC%BA/code/%E7%9F%A5%E4%B9%8E%E5%A2%9E%E5%BC%BA.user.js debugger eval code:1:60
https://github.com/XIU2/UserScript debugger eval code:1:60
https://greasyfork.org/en/scripts/419215-%E8%87%AA%E5%8A%A8%E6%97%A0%E7%BC%9D%E7%BF%BB%E9%A1%B5/feedback#post-discussion debugger eval code:1:60
https://greasyfork.org/en/reports/new?item_class=script&item_id=419215 debugger eval code:1:60
https://www.jsdelivr.com/package/gh/XIU2/UserScript debugger eval code:1:60
https://www.discuz.net/ debugger eval code:1:60
https://www.phpbb.com/community/ debugger eval code:1:60
https://xenforo.com/community/ debugger eval code:1:60
https://demo.nexusphp.org/ debugger eval code:1:60
https://discuss.flarum.org/ debugger eval code:1:60
https://www.axiuno.com/ debugger eval code:1:60
https://www.google.com/ debugger eval code:1:60
https://cn.bing.com/ debugger eval code:1:60
https://www.baidu.com/ debugger eval code:1:60
https://www.sogou.com/ debugger eval code:1:60
https://weixin.sogou.com/ debugger eval code:1:60
https://www.toutiao.com/ debugger eval code:1:60
https://m.sm.cn/ debugger eval code:1:60
https://www.wuzhuiso.com/ debugger eval code:1:60
https://www.so.com/ debugger eval code:1:60
https://searx.owlook.com.cn/ debugger eval code:1:60
https://duckduckgo.com/ debugger eval code:1:60
https://www.startpage.com/ debugger eval code:1:60
https://yandex.com/ debugger eval code:1:60
https://search.yahoo.com/ debugger eval code:1:60
https://www.qwant.com/ debugger eval code:1:60
https://www.ecosia.org/ debugger eval code:1:60
https://goobe.io/ debugger eval code:1:60
https://magi.com/ debugger eval code:1:60
https://www.qingsearch.com/ debugger eval code:1:60
https://www.ask.com/ debugger eval code:1:60
https://tieba.baidu.com/ debugger eval code:1:60
https://movie.douban.com/ debugger eval code:1:60
https://www.zhihu.com/ debugger eval code:1:60
https://weibo.com/ debugger eval code:1:60
https://bbs.tianya.cn/ debugger eval code:1:60
https://bbs.hupu.com/ debugger eval code:1:60
https://bbs.nga.cn/ debugger eval code:1:60
https://v2ex.com/ debugger eval code:1:60
https://jandan.net/ debugger eval code:1:60
https://www.mysmth.net/ debugger eval code:1:60
https://www.lkong.com/ debugger eval code:1:60
https://bbs.pediy.com/ debugger eval code:1:60
https://bangumi.tv/ debugger eval code:1:60
https://www.dongchedi.com/car_fans_community debugger eval code:1:60
https://club.kdslife.com/ debugger eval code:1:60
https://www.libaclub.com/ debugger eval code:1:60
https://www.taoguba.com.cn/ debugger eval code:1:60
https://bbs.lieyou888.com/ debugger eval code:1:60
https://lowendtalk.com/ debugger eval code:1:60
https://rutracker.org/ debugger eval code:1:60
https://adnmb3.com/ debugger eval code:1:60
https://search.bilibili.com/ debugger eval code:1:60
https://www.pixiv.net/ debugger eval code:1:60
https://www.vilipix.com/ debugger eval code:1:60
https://www.pixivision.net/ debugger eval code:1:60
https://www.zcool.com.cn/ debugger eval code:1:60
https://www.58pic.com/ debugger eval code:1:60
https://588ku.com/ debugger eval code:1:60
https://www.nipic.com/ debugger eval code:1:60
https://www.ztupic.com/ debugger eval code:1:60
https://www.ooopic.com/ debugger eval code:1:60
https://ibaotu.com/ debugger eval code:1:60
https://818ps.com/ debugger eval code:1:60
https://pixabay.com/ debugger eval code:1:60
https://www.logosc.cn/so/ debugger eval code:1:60
http://www.sccnn.com/ debugger eval code:1:60
https://www.iconfont.cn/ debugger eval code:1:60
https://iconarchive.com/ debugger eval code:1:60
https://mixkit.co/ debugger eval code:1:60
https://www.puxiang.com/ debugger eval code:1:60
https://www.xuexiniu.com/ debugger eval code:1:60
https://www.om.cn/ debugger eval code:1:60
http://www.xiadele.com/ debugger eval code:1:60
https://www.3dmgame.com/ debugger eval code:1:60
https://www.ali213.net/ debugger eval code:1:60
https://www.gamersky.com/ debugger eval code:1:60
https://mod.3dmgame.com/ debugger eval code:1:60
https://www.curseforge.com/ debugger eval code:1:60
https://www.nexusmods.com/ debugger eval code:1:60
https://steamcommunity.com/workshop/browse/?appid=550&browsesort=trend&section=readytouseitems debugger eval code:1:60
https://steamworkshopdownloader.io/ debugger eval code:1:60
http://steamworkshop.download/ debugger eval code:1:60
https://steamcommunity.com/ debugger eval code:1:60
https://www.yikm.net/ debugger eval code:1:60
https://switch520.com/ debugger eval code:1:60
https://cs.rin.ru/forum/viewforum.php?f=10 debugger eval code:1:60
https://byrut.org/ debugger eval code:1:60
https://crackhub.site/ debugger eval code:1:60
https://fitgirl-repacks.site/ debugger eval code:1:60
https://masquerade.site/ debugger eval code:1:60
https://www.cupfox.app/ debugger eval code:1:60
https://www.novipnoad.com/ debugger eval code:1:60
https://ddrk.me/ debugger eval code:1:60
https://www.nfmovies.com/ debugger eval code:1:60
https://www.zxzjtv.com/ debugger eval code:1:60
https://www.pianba.tv/ debugger eval code:1:60
https://enlienli.com/ debugger eval code:1:60
https://mjw21.com/ debugger eval code:1:60
https://www.zhenbuka3.com/ debugger eval code:1:60
http://www.zzzfun.com/ debugger eval code:1:60
https://www.tucao.one/ debugger eval code:1:60
http://www.imomoe.live/ debugger eval code:1:60
http://www.yxdm.li/ debugger eval code:1:60
http://www.nicotv.me/ debugger eval code:1:60
https://www.mandao.tv/ debugger eval code:1:60
https://www.agemys.com/ debugger eval code:1:60
https://www.dm233.cc/ debugger eval code:1:60
https://anime1.me/ debugger eval code:1:60
https://www.yinfans.me/ debugger eval code:1:60
https://pianyuan.org/ debugger eval code:1:60
http://clg.im/ debugger eval code:1:60
https://www.yuhuage52.xyz/ debugger eval code:1:60
https://btbtt20.com/ debugger eval code:1:60
https://www.bd2020.com/ debugger eval code:1:60
https://gaoqing.fm/ debugger eval code:1:60
https://www.kisssub.org/ debugger eval code:1:60
https://share.acgnx.net/ debugger eval code:1:60
https://www.acgnx.se/ debugger eval code:1:60
https://share.dmhy.org/ debugger eval code:1:60
https://dmhy.anoneko.com/ debugger eval code:1:60
https://www.36dm.club/ debugger eval code:1:60
https://bt.acgzero.com/ debugger eval code:1:60
https://acg.rip/ debugger eval code:1:60
https://bangumi.moe/ debugger eval code:1:60
https://banguami.moe/lite debugger eval code:1:60
https://miobt.com/ debugger eval code:1:60
https://skrbtga.xyz/ debugger eval code:1:60
https://nyaa.si/ debugger eval code:1:60
https://yts.mx/ debugger eval code:1:60
https://1337x.to/ debugger eval code:1:60
https://rarbg.to/ debugger eval code:1:60
https://zooqle.com/ debugger eval code:1:60
https://kickasss.to/ debugger eval code:1:60
https://webhd.cc/ debugger eval code:1:60
https://www.mini4k.com/ debugger eval code:1:60
https://trackerslist.com/ debugger eval code:1:60
https://www.a4k.net/ debugger eval code:1:60
https://subhd.tv/ debugger eval code:1:60
https://assrt.net/ debugger eval code:1:60
http://www.ddzimu.com/ debugger eval code:1:60
https://cn.zimuzimu.com/ debugger eval code:1:60
https://zimuku.org/ debugger eval code:1:60
https://www.manben.com/ debugger eval code:1:60
https://www.haoman6.com/ debugger eval code:1:60
http://www.sixmh7.com/ debugger eval code:1:60
https://www.cartoonmad.com/ debugger eval code:1:60
https://www.dongman.la/ debugger eval code:1:60
http://www.manmanju.com/ debugger eval code:1:60
https://www.maofly.com/ debugger eval code:1:60
https://www.manhuapi.com/ debugger eval code:1:60
https://www.manhuaren.com/ debugger eval code:1:60
https://www.mhgui.com/ debugger eval code:1:60
https://www.36manga.com/ debugger eval code:1:60
https://www.imanhuaw.net/ debugger eval code:1:60
https://www.manhuadb.com/ debugger eval code:1:60
https://www.hicomic.net/ debugger eval code:1:60
https://www.dmzj.com/ debugger eval code:1:60
https://manhua.dmzj.com/ debugger eval code:1:60
http://www.alimanhua.com/ debugger eval code:1:60
https://www.kanbook.net/ debugger eval code:1:60
https://manhua.dmzj.com/ debugger eval code:1:60
https://comic.acgn.cc/ debugger eval code:1:60
https://www.ykmh.com/ debugger eval code:1:60
https://copymanga.net/ debugger eval code:1:60
https://www.omyschool.com/ debugger eval code:1:60
http://www.mhxqiu1.com/ debugger eval code:1:60
http://manhua.fffdm.com/ debugger eval code:1:60
https://www.webmota.com/ debugger eval code:1:60
https://www.leyuman.com/ debugger eval code:1:60
https://www.77mh.xyz/ debugger eval code:1:60
http://www.ccshwy.com/all/ debugger eval code:1:60
https://www.gufengmh9.com/ debugger eval code:1:60
https://www.szcdmj.com/ debugger eval code:1:60
https://mangabz.com/ debugger eval code:1:60
https://www.xmanhua.com/ debugger eval code:1:60
https://www.cocomanga.com/ debugger eval code:1:60
https://www.qidian.com/ debugger eval code:1:60
https://www.qimao.com/ debugger eval code:1:60
http://zxcs.me/ debugger eval code:1:60
https://www.baoshuu.com/ debugger eval code:1:60
https://www.yushubo.com/ debugger eval code:1:60
https://www.owlook.com.cn/ debugger eval code:1:60
https://www.23qb.com/ debugger eval code:1:60
https://www.xineyby.com/ debugger eval code:1:60
https://m.xiaoshuo77.net/ debugger eval code:1:60
https://www.linovelib.com/ debugger eval code:1:60
https://w.linovelib.com/ debugger eval code:1:60
https://www.ihuaben.com/ debugger eval code:1:60
https://www.linovel.net/ debugger eval code:1:60
https://archiveofourown.org/ debugger eval code:1:60
https://yuedu.xiu2.xyz/ debugger eval code:1:60
https://www.lan-sha.com/ debugger eval code:1:60
https://iao.su/ debugger eval code:1:60
https://www.sharerw.com/ debugger eval code:1:60
https://www.extfans.com/ debugger eval code:1:60
https://www.macwk.com/ debugger eval code:1:60
https://www.appinn.com/ debugger eval code:1:60
https://www.isharepc.com/ debugger eval code:1:60
https://www.ghxi.com/ debugger eval code:1:60
https://www.6yit.com/ debugger eval code:1:60
http://www.apprcn.com/ debugger eval code:1:60
https://www.weidown.com/ debugger eval code:1:60
https://www.dayanzai.me/ debugger eval code:1:60
https://www.423down.com/ debugger eval code:1:60
https://fsylr.com/ debugger eval code:1:60
https://www.iplaysoft.com/ debugger eval code:1:60
http://www.mubolin.cn:99/ debugger eval code:1:60
https://www.mpyit.com/ debugger eval code:1:60
https://www.tenlonstudio.com/ debugger eval code:1:60
https://www.yxssp.com/ debugger eval code:1:60
https://www.nite07.com/ debugger eval code:1:60
https://www.sordum.org/ debugger eval code:1:60
https://winaero.com/ debugger eval code:1:60
https://lrepacks.net/ debugger eval code:1:60
https://dlandroid.com/ debugger eval code:1:60
https://www.winhelponline.com/blog/ debugger eval code:1:60
https://www.windowslatest.com/ debugger eval code:1:60
https://www.thewindowsclub.com/ debugger eval code:1:60
https://onlinelibrary.wiley.com/ debugger eval code:1:60
https://pubs.acs.org/ debugger eval code:1:60
https://libgen.rs/ debugger eval code:1:60
https://www.sciencedirect.com/ debugger eval code:1:60
https://z-lib.org/ debugger eval code:1:60
https://pubmed.ncbi.nlm.nih.gov/ debugger eval code:1:60
https://www.x-mol.com/ debugger eval code:1:60
http://www.cqvip.com/ debugger eval code:1:60
https://www.ablesci.com/ debugger eval code:1:60
https://www.coolkeyan.com/ debugger eval code:1:60
http://muchong.com/bbs debugger eval code:1:60
https://xueshu.baidu.com/ debugger eval code:1:60
https://cn.bing.com/academic debugger eval code:1:60
https://scholar.google.com/ debugger eval code:1:60
https://sc.panda321.com/ debugger eval code:1:60
https://xs2.dailyheadlines.cc/ debugger eval code:1:60
https://output.nsfc.gov.cn/ debugger eval code:1:60
https://stackoverflow.com/ debugger eval code:1:60
https://segmentfault.com/ debugger eval code:1:60
https://www.w3cschool.cn/ debugger eval code:1:60
https://www.w3school.com.cn/ debugger eval code:1:60
https://www.runoob.com/ debugger eval code:1:60
https://www.cnblogs.com/ debugger eval code:1:60
https://www.51cto.com/ debugger eval code:1:60
https://gitee.com/ debugger eval code:1:60
https://www.sciencealert.com/ debugger eval code:1:60
https://www.guokr.com/ debugger eval code:1:60
https://www.landian.vip/ debugger eval code:1:60
https://kenengba.com/ debugger eval code:1:60
https://www.expreview.com/ debugger eval code:1:60
https://www.ithome.com/ debugger eval code:1:60
https://36kr.com/ debugger eval code:1:60
https://www.imdb.com/ debugger eval code:1:60
https://www.rottentomatoes.com/ debugger eval code:1:60
https://zhutix.com/ debugger eval code:1:60
https://lanzou.com/ debugger eval code:1:60
https://www.xinpianchang.com/ debugger eval code:1:60
https://zh.wikihow.com/ debugger eval code:1:60
https://www.afreecatv.com/ debugger eval code:1:60
https://www.userscript.zone/ debugger eval code:1:60
https://userstyles.world/ debugger eval code:1:60
https://getquicker.net/ debugger eval code:1:60
https://repo.xposed.info/module-overview debugger eval code:1:60
https://www.bookmarkearth.com/ debugger eval code:1:60
https://www.smzdm.com/ debugger eval code:1:60
https://www.meidebi.com/ debugger eval code:1:60
https://www.jiligamefun.com/ debugger eval code:1:60
https://pic.netbian.com/ debugger eval code:1:60
https://bing.ioliu.cn/ debugger eval code:1:60
https://konachan.net/ debugger eval code:1:60
https://anime-pictures.net/ debugger eval code:1:60
https://hdqwalls.com/ debugger eval code:1:60
https://www.nastol.com.ua/ debugger eval code:1:60
https://www.snapmail.cc/ debugger eval code:1:60
https://pan.lanzouo.com/b073l8d1e debugger eval code:1:60
https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepeloendndfphd?hl=zh-CN debugger eval code:1:60
https://zhuanlan.zhihu.com/p/276027099
