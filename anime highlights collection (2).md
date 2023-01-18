---
title: 影视/番剧素材查找 番剧精彩片段制作 create bangumi/anime highlights collection
created: '2023-01-16T06:20:31.260Z'
modified: '2023-01-18T13:53:03.156Z'
---

# 影视/番剧素材查找 番剧精彩片段制作 create bangumi/anime highlights collection

观众情绪是唯一的标准。

-------

影视剪辑比较杂乱 现在喜欢随便混搭 意识流剪辑 当然拿来做一般的素材也行 不过就需要自己搭建处理了

爱奇艺有以图搜片 不过只能搜爱奇艺有版权的

[33台词](https://33.agilestudio.cn/) 根据电影台词来搜索电影出处 同时有[根据画面描述搜索视频片段](https://fse.agilestudio.cn/)

[film.ai](https://beta.flim.ai/) now can query screenshot and movie name by description and download thumbnails of movies (not latest, not mainland), but without subscription you cannot get accurate seek time (though it will never be accurate)

in [imdb](https://www.imdb.com) can pass film/anime name in multiple languages and get the english name (and trailer video), then query for it in [1337x](https://1337x.to/) (results sorted by seeder counts)

-------

准备片头和片尾 准备视频模版 每个片段不要太长 选取多个番剧 适当处理视频 防止撞车

如果要剪短视频 多用转场效果 提取正在说话 动作幅度大 或者模型认为比较高能的片段

首先收集b站的[动漫高能剪辑视频](https://www.bilibili.com/video/BV1e54y1y7qy)

提取标题 标签 封面

寻找类似封面 根据封面生成标签 或者根据标签寻找封面 (视频里面找 或者类似图片)

训练根据封面和标签生成标题的模型 或者自行发挥 尝试 只要看起来还行

分段分析视频片段 用yolo找出视频正在播放的区域 方便裁剪识别动漫

识别截图中的文字 查看是否有重复的 包含有番剧名称 可以用来查找动漫

asoul database有[识别截图出处](https://github.com/A-Soul-Database/PhotoSearch/blob/42ce7f8877938b52cbcae6a61edb90a547894a23/main.py)的思路

[asoul自动操作Windows上面剪映获取字幕](https://github.com/A-Soul-Database/JianYingSrtServer) [剪映API](https://github.com/P-PPPP/JianYingApi)基于pyautogui 可以使用免费的CI系统 在云端windows机器上面运行程序

利用动漫素材来源定位网站可以锁定剪辑位置 裁剪时间长度要控制 只选取匹配度高的 NSFW的不要 另外图像尺寸要合适 要正好是视频截图 注意网上的图片不一定是视频截图 最好直接在视频里面找 不要裁剪 图片可能加了一些番剧没有的字符或者装饰 ([saucenao](https://saucenao.com/)>75 (能识别出来老番 比如“没有钱” 但是老番一般没啥人做种 下载可能很慢 不如直接放弃 有几率搜出来pixiv的插画 显然不能拿来剪视频), [trace.moe](https://trace.moe)>75, both can detect latest (ongoing) bangume, select top-most) 如果匹配度不高就算了 找下一个 即使匹配度高也要充分怀疑 同一段视频的某段区域 多截图几次 如果出来的不是同一个番 或者不是同一个番的同一集 或者不是连续的时间段 (分别探讨以上情况 如果是番剧的开始/结束片段那么可能同时出现在多个分集里面 如果确实是开头公用的画面 必然会反复出现相同番剧的名字 在这种情况下 优先选取之前已经下载过的视频) 那么就说明结果不对头 即使验证通过 也得对剪出来的片段进行二次验证 检测片段是否存在那个画面 当然对于快速切换画面的 确实有大量不同番剧片段出现在同一个视频的 那就有待进一步探讨了

这种种子文件下载得到的视频 往往带有字体文件 可以收集用来做视频 封面设计

番剧搜索引擎里面出现的问题 比如不同番剧相似画面的相似度不应该那么高 可以通过自监督强化学习解决 另外画面裁剪的问题 (画中画 裁剪小了或者大了 或者有画面延伸) 都需要进一步改进 最主要的还是要有大量的 不断更新的数据 当然目前来看这些不需要处理

因为大家都喜欢看中文字幕 (谁听得懂日语 或者一边听日语一边看英文字幕啊) 尽量不用国外的片源 如果只有国外的 直接机器翻译能找到的公开字幕 或者直接语音转文字 图片转文字 不过话说回来 种子下载慢 国内网站广告又多 如果能[单独下载字幕](https://github.com/foxofice/sub_share) (vcb的有单独分开的字幕可以下载) 对得上时间长度的话 就可以获取到带字幕的老番

anime downloaders: (hard to find chinese subtitles huh?)

[animdl](https://github.com/justfoolingaround/animdl) supports time ranges
[monkey-dl](https://github.com/Oshan96/monkey-dl)
[ani-cli](https://github.com/pystardust/ani-cli) ([animixplay](https://animixplay.to/) is gone, fixing?)
[gogoanime-api](https://github.com/riimuru/gogoanime-api) in which you may not get raw video with japanese dub
[jerry](https://github.com/justchokingaround/jerry) with subtitle language specification

下载下来之后 得到视频字幕 进行标记 (打上标签) 方便以后创作类似视频的时候查找 以及作为数据集 训练模型 根据字幕/弹幕 (弹幕得去b站找并且自行提取) 或者结合视频内容 (算力够么 需要人肉标记 还是反复调用识图API进行标记 或者用jina (fine-tuned?) 计算图像相似度) 预测不同类型高能片段的标签

老番可以在国内番剧网站寻找 b站有免费的那么可以尝试下载

[tracker list for anime](https://github.com/DeSireFire/animeTrackerList)

种子站要能够根据seeder降序排序 [vcb](https://vcb-s.com/)的一般seeder会很多 但是其他字幕组的新番即使seeder比较少 下载速度也会很快 看情况而定 vcb只负责压制 其他字幕组提供单独分开的字幕 两者要单独下载 [Nyaa](https://nyaa.si/)支持该功能 [Nyaa API](https://github.com/Kylart/Nyaapi) 这个站将番剧分类为原盘 英文翻译版 其他语言翻译版 中文翻译属于其他语言翻译版 如果要找中文翻译版本 先选定类型 然后查找文件名是否包含指定代号 有字幕文件的话先下载看看 检测下主语言类别

aria2c can be controlled via python (to make sure it will exit immediately after finishing download instead of seeding and blocking, though can be achieved with some tweaks on commandline arguments to execute command after download finished signal emitted): [aria2p](https://github.com/pawamoy/aria2p) (can be used both as a library or cli program), [pyaria2](https://github.com/zhenlohuang/pyaria2) (old) searching aria2 in github, i found some repos relating to baidunetdisk.

到[国内番剧种子站](https://www.bilibili.com/read/cv7338766/)去找片源 (这些站基本一个样) 新番下载较快 老番下载会非常慢 几乎龟速 (检查有没有seeder 一个都没有就别想下了 直接放弃 以及监控下载进度 一段时间没有进度基本凉了) 而不是一些在线观看的网站 (视频不清晰 还有广告在里面) 由于没法用yt-dlp选取段落下载 最好用云电脑下载然后回传 关掉aria2c的做种选项 下完自动关闭 如果是合集 需要[选择指定的对象进行下载](https://github.com/aria2/aria2/issues/843)

```bash
aria2c --show-files target.torrent
aria2c -x 16 --file-allocation=none --select-file=<file_index> target.torrent
```

得到了番剧命名格式之后建议利用第三方搜索引擎搜索

这些种子站一般都会把新番做成rss 用来订阅 做新番推荐比较合适 需要找到番剧介绍的文章来转化 资源的名称遵循某种格式 番剧名称会用不同语言标注 提示字幕的格式 番剧番号用空格 英文或者中文括号括住 一般至少两位数 小于两位会补零 海边的异乡人之类的只有一集 没有episode提示

如果要实时看云电脑的进度可以自己搭建一个netprogressbar server 根据约定好的url和密码 (read-only and write-only password, or both, by setting different privilege) 来上报和接收进度 server要及时回收资源

番剧信息包括名称 类型 标签 具体第几话 单季和多季有别 如果是多季的话需要研究如何找出来 提取名字要完整 如果有续集 (比如"Yahari Ore no Seishun Lovecome wa Machigatte Iru.") 那么要改进parse逻辑 准确识别

有[提取画面中动漫人物信息以及所属番剧的网站](https://ai.animedb.cn) [Python API](https://github.com/itoukou1/zhenxun_plugin_animetrace/blob/main/__init__.py) 只支持日漫 [该网站在b站的使用方法介绍](https://www.bilibili.com/read/cv17700107) 注册码目前是`hello2023` 可以用来做单个人物合集 在发送截图之前先用模型扫描一下到底有没有动漫人脸 如果没有就不用上传了 识别不出来

trailer也可以用来训练视频摘要模型 提取番剧精彩片段 可以作为素材
