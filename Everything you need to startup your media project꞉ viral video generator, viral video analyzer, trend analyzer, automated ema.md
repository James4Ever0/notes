---
title: 'Everything you need to startup your media project: viral video generator, viral video analyzer, trend analyzer, automated email account registration, download only a portion of video, peek video screenshots'
created: '2023-01-09T03:22:12.000Z'
modified: '2024-02-28T13:53:35.693Z'
---

# Everything you need to startup your media project: viral video generator, viral video analyzer, trend analyzer, automated email account registration, download only a portion of video, peek video screenshots

Microsoft powered [recommendation system](https://github.com/recommenders-team/recommenders), has now joined the Linux Foundation.

---

image/anime background removal system:

https://pypi.org/project/rembg

---

CantoonSegmentation can be used for creating visual effects over static cartoon images.

---

use grammar or state machine to constraint how llm generate tokens, in order to perform actions and call tools correctly

---

remove vocal from video and from music downloaded from web, then execute shazam. or only remove vocal from video and execute music search.

---

[voice auto translation](https://github.com/facebookresearch/seamless_communication) by meta

---

use attention visualization to create pan effects, focus on different parts and illustrate separately

---
to get response fast, you need to create content fast. sometimes it is important to degrade aspects like resolution and more.

---

https://github.com/audio-agi/audiosep

[changedetection](https://github.com/dgtlmoon/changedetection.io) get website updates

[longlora](https://github.com/dvlab-research/LongLoRA)

自动删评机器人：

根据对类似内容的评论预期（结合大模型）进行删除

根据情感分析删除不利评论

----

根据视频内容 标题调整封面人物表情

----

造仿制b站 收集用户点击数据

----

b站禁用了手机端搜索接口的页面数目，但没有限制电脑端搜索页面数目，估计是为了避免二创素材收集不受影响。

----

[deep danbooru](https://dambooru.donmai.us) for anime comprehension, scene understanding etc

----

Do not use removable drives (NAS?) as scratch/data disk for long-term programs. Instead, use internal drives.

If possible, first sync all necessary files from removable drives to internal disk, then run the long-running program from there, or first run from rootfs, then jump to removable drives. When error occurs, check if disk is unmounted, try different methods to reload them and rerun the program.

Another possible cause is insufficient current. Check for similar issues online.

----

短视频内部模拟不同视频上下翻页效果

----

如果封面提取关键词进行训练并更换 尝试自己生成配图和文字的方法难以实现 可以考虑更换字体和色彩 文字内容不变

封面文字遵循一定的阅读顺序 从上到下 从左到右 可以设立排版以及合并（用于训练）规则

----

youtube now can auto generate video chapters, which might be part of text/video summarization.

multinational, multilingual, subtitles, localizations

---- 

models for content generation:

[one-for-all](https://github.com/OFA-Sys/OFA) multi-modal generation

[magma](https://github.com/Aleph-Alpha/magma): a GPT-style multimodal model that can understand any combination of images and language

----

[视频创作导航](https://www.aewz.com/) 可以用来找自动化创作视频的思路

[字由](https://www.hellofont.cn/font-list) 识别字体 下载免费字体

[Startup Toolbox](https://github.com/alexanderisora/startuptoolbox/blob/master/README.md)

tools for startup companies, including:

```
[Website]
[Design]
[Support and customer communication]
[Payments, billing and distribution]
[User Analytics and Reporting]
[Business Analytics]
[Automation]
[HR and Payroll]
[Forms and Surveys]
[Tech]
[Product building]
[Marketing and growth]
[Collaboration]
[Build a chatbot]
[Domains and naming]
[Legal, Account and Invoicing]
[Funding]
[Sales]
[Communities]
[Learn]
[A/B testing]
[Launch]
[Other]
```

[Awesome Streaming](https://github.com/VertioseLabs/Awesome-Streaming)

a list of live streaming and content creation tools:

```
[Content Creation]
[Sponsors And Affiliate]
[Setup Guides]
[Branding]
[Discord Creation]
[Brand Website]
[Uncopyrighted Music]
[FPS Accuracy]
[Subathon Framework]
[Video Editing]
[OpSec]
[Stat Tracking]
[Game Development]
[V-Tubing]
[How To Start An LLC]
```

收集大up主的名字 根据提取出来的名词 清除文案中的含有名字的句子

for information cascade, treat recommendation system as your target data, and fit your content into the prediction of "to-view" video of popular videos

分析弹幕关键词是否与大量其他视频标题相重合

B站撞车搬运检测：

油管有带有英文番剧名称的AMV/MAD剪辑

通过B站搜索Weibo Tumblr Tiktok Youtube的视频ID 或者名称，可以找出视频是否被转载

通过搜索其他网站的前缀 比如`https://www.youtube.com` 可以得到被转载视频的链接 但是感觉数据不是很靠谱 不是很火的那种 要看大流量的还是得爬首页推荐链接 根据话题搜索

## video highlights extraction

although you may want to train/extract that manually, it would sure be tedious and not self-updating (unless using reinforcement learning).

often we determine highlights by sound, visual and voice together. highlights often can be identified without too much context, so it can be chunk based.

### bilibili

[b站的高能进度条](https://github.com/SocialSIsterYi/bilibili-API-collect/blob/master/video/pbp.md) 在油管被叫做"most replayed"

b站有弹幕 所以可以根据弹幕找到精彩片段 [VClimax](https://github.com/baolintian/VClimax)是一个浏览器插件 可以通过弹幕单位时间增长速率，设置相关的阈值，来定位最精彩的内容 (弹幕密度怕还是得要分析) 跳转部分番剧OP 视频搞笑片段精准定位 (怕还得是要机器学习)

[bilibili Danmaku Skip](https://github.com/ZhangEliot/bilibiliDanmuSkip) is another browser plugin which will identify highlights by analyzing danmaku with parameters like threshold, interval and bias

### youtube

youtube's most played data can be extracted by:

[youtube-heatmap](https://www.npmjs.com/package/youtube-heatmap) (nodejs, using puppeteer (bad!))

[youtube operational api](https://github.com/Benjamin-Loison/YouTube-operational-API)'s (powered by shared API keys and info extractors without key), while apparantly [youtube-most-replayed](https://github.com/Woojin-Choi/youtube-most-replayed/blob/master/src/App.js) is using this service to retrieve the data from [yt.lemonslife.com](https://yt.lemnoslife.com) powered by this library

[heatmap extractor](https://github.com/Benjamin-Loison/YouTube-operational-API/blob/main/videos.php)

[youtube.js](https://github.com/LuanRT/YouTube.js) (reverse engineered innertube api) added [support for chapters and video heatmap](https://github.com/LuanRT/YouTube.js/pull/263)

## youtube-dl search youtube video

```bash
youtube-dl "ytsearch[optional_result_limit]:[query]"

# pass query url directly to allow pagination or filters

youtube-dl "https://www.youtube.com/results?search_query=how+to+create+android+app+in+android+studio&page=1"
```

## record live streaming video, upload video

### [biliup](https://github.com/biliup/biliup/) & [biliup-rs](https://github.com/ForgQi/biliup-rs) (commandline program)

全自动录播、投稿工具，也支持twitch、ytb频道搬运。提供分p上传b站接口

其实直播回放没有什么好看的 很单调 另外b站上传之后可以获得视频预测标签

### [youtube automation toolkit](https://github.com/wanghaisheng/youtube-automation-toolkit) post same content to multiple platforms: bilibili, douyin, douyu, instagram, reddit, spotify, tiktok, twitch

though the idea is correct by posting original content to multiple platforms to prevent pirating, but the description/title generation is a vital part of the process, which must be done intelligibly (AI or human). as for now the repo is just full of links. if you want tools you click given link.

## Download a portion of video

### yt-dlp (latest)

check `pyjom/tests/download_sections_video_portion_partial_download_youtube_yt_dlp_bilibili/test_bilibili.sh` for advanced usage of yt-dlp and more on bilibili parsing.

**SINCE YT-DLP IS UPDATED YOU CAN USE `--download-sections` ARGUMENT FOR YOUTUBE** 

If you want to download multiple sections of same video, you must specify video output format string via `-o`

But when using that without "--force-keyframes-at-cuts" (skip re-encoding which can speed up thing but not ensuring quality of video at tail), you better keep margin at tail for 10 seconds (could glitch at last 5 seconds) and head for 5 seconds (maybe head margin is not needed?).

### youtube-dl

first acquire download url: `youtube-dl [--youtube-skip-dash-manifest] [-f 18] -g "https://www.youtube.com/watch?v=V_f2QkBdbRI"` (you need to force the format.)

then use ffmpeg with the url to chop the slice: `ffmpeg -ss 00:00:15.00 -i "OUTPUT-OF-FIRST URL" -t 00:00:10.00 -c copy out.mp4`

### [RangeDownloader](https://github.com/A-Soul-Database/RangeDownloader) by A-Soul-Database

A-Soul-Database is a live-streaming replay record database designed for vtubers, organized in some way for easy information retrieval.

RangeDownloader is acting like a server, though sometimes we are not sure how fast(er) it can really be.

## Viral videos

### Data sources and monitors

#### [Rebang.today](https://www.rebang.today)

通过B站推荐标签接口可以得到观众的实时需求

提供全站 知乎 微博 IT之家 百度 虎扑 直播吧 少数派 36氪 吾爱破解 天涯 小众软件 反斗限免 哔哩哔哩 抖音 技术期刊 v2ex GitHub的热榜

API：`https://api.rebang.today/v1/items?tab=<TAB_NAME>&page=<PAGE_NUM>` (potential parameters: sub_tab, date_type (default:now))

知乎有个专门的热榜，地址：`https://www.zhihu.com/billboard`

[知乎圆桌](https://www.zhihu.com/roundtable) [知乎发现](https://www.zhihu.com/explore)

| name | tab |
| --- | ---  | 
|  全站热榜  | top-all |
| 微博 | weibo |
| V2EX | v2ex | 
| 知乎 | zhihu | 
| 哔哩哔哩  | bilibili|
| GitHub |  github|
| 抖音 | douyin|
| 技术期刊  |journal-tech|
| 虎扑|  hupu|
| 少数派  | sspai|
| 百度  | baidu|
| 36氪  | 36kr|
| 天涯 |  tianya|
| 吾爱破解 | 52pojie|
| IT之家 | ithome|
|全站24小时  | top-daylong|
|直播吧 | zhibo8|
|小众软件   |appinn|
|反斗限免|  apprcn|

#### [番茄数据](https://www.tomatodata.cn/news/1355.html)

番茄数据提供了从近24小时--近90天B站的最新热门视频，你既可以通过“搜索标题、简介、标签、评论出现关键词”，也可以通过行业分类、播放数、点赞数、投币数、视频时长、观众画像等高级条件，精准定位想要查找领域的热门视频。传播指数的计算方法有待研究。传播指数是根据UP主的粉丝数、视频点赞数、播放数、投币数、分析数等分析出来的综合得分。根据评论热词分析视频观众热点，根据评论用户分析用户画像。

对于各大数据网站 都存在一个收录的接口 如果up主从来没有上过首页 大概率不会被收录 需要手动提交 间接说明大up主是如何被找到的

### Image recognizers

#### [Baidu Image recognizer](https://github.com/chenguanyou/BaiduSerchImgApi) 百度识图

与此相关的识图项目位置：`pyjom/tests/search_engine_suggestion_based_qa_bot`

可以获取关键字，标签，同样的图，秒懂百科视频，百度百科数据，包含图片的信息，颜值信息

通过把上传接口修改 以及http改成https 现在可以继续使用

位置：`pyjom/tests/viral_video_experiments/BaiduSerchImgApi`

通过http改成https 修改好了[360识图的接口](https://github.com/chenguanyou/360ImageSearch)

位置：`tests/viral_video_experiments/360ImageSearch`

### Video collectors

#### [tiktok compilation video generator](https://github.com/HA6Bots/TikTok-Compilation-Video-Generator)

collect popular video on tiktok by multiple filters such as hashtags, categories , popularities and search queries

#### [WeiboSpider](https://github.com/nghuyong/WeiboSpider)

需要cookie 收集用户信息 用户粉丝列表 用户关注列表 微博采集 微博评论采集 微博转发采集 基于关键词的微博检索

#### [botTuber: a instagram compilation reposter to youtube](https://github.com/sam5epi0l/BotTuber)

Using `instaloader` and `instalooter`, it can download videos from instagram. It merges a series of video and add intro and outro. It only contains one default title starts with "TRY NOT TO LAUGH" in its "auto" mode.

#### [reddit hot videos to youtube](https://github.com/spantheslayer/yt-upload-automation)

In "TiktokCringe" reddit channel, we are able to get hot posts and video links prefixed by `https://v.redd.it` (from tiktok to reddit) in json format: `https://www.reddit.com/r/TikTokCringe/hot.json?limit=12`. This link looks like some API or subscription. Maybe Bilibili and other sites have similar "hot" json urls. The way to extract video links is in [atmt.sh](https://github.com/spantheslayer/yt-upload-automation/blob/main/atmt.sh). It adds transitions to every video clip.

### Video editors

#### [vced](https://github.com/datawhalechina/vced)

i think it needs to be fine-tuned on large diversive training data.

VCED 可以通过你的文字描述来自动识别视频中相符合的片段进行视频剪辑。该项目基于跨模态搜索与向量检索技术搭建，通过前后端分离的模式，帮助你快速的接触新一代搜索技术。

#### [videofy](https://github.com/mohtamohit/Videofy)

it is a self-hosted service, summarize article, get relevant text and image, determine mood to select BGM. try for yourself!

#### [meme video maker](https://github.com/FOLLGAD/meme-video-maker/blob/a9bc7bc3f804da05353faa23fde56cff410f16bb/server/src/video.ts)

It uses google cloud to select "English" words on image, enable the user to edit the "stage" to show meme step by step.

It requires amazon cloud services and google cloud services.

#### [回声工坊 TRPG Replay Generator](https://github.com/DanDDXuanX/TRPG-Replay-Generator)

TRPG：桌上角色扮演游戏 有丢骰子（随机元素）的RPG

角色立绘可以是动态的 但是是多个png文件

背景可以设定为 `{'black','white','greenscreen'}` 中的一个，以建立纯色背景

Has special requirements to media sources. Use `.ogg` format for BGM. Use `.wav` format for AFX and voices. Use `.png` for image. Cannot get background video layers working so you might consider some "green screen" effects.

Use `--ExportVideo` flag to export video without GUI.

#### openshot and libopenshot (for python bindings)

[Nightcorify](https://github.com/thomashuss/nightcoreify/blob/545265c054c0d127b6dd81d4038f56c8c092a739/nightcorei.py#L38) is accelerating audio and raising pitch (`asetrate` strenches the timeline to change sample rate, `atempo` (not used in here) change the timeline but not the pitch, while `aresample` changes the sample rate but not timeline), also showing audio wave shape with `showwaves`.

This library is complex **AND WITHOUT PROPER DOC FOR PYTHON** thus not recommend for using

#### [keybert and summarization transformer pipeline](https://github.com/pawanreddy-u/videocreation/blob/main/generateVideo.py)

Check [docs on transformers pipelines](https://huggingface.co/transformers/v4.10.1/_modules/transformers/pipelines.html) for default and fine-tuned task-specific models for each pipeline.

[Keybert](https://pypi.org/project/keybert/) uses "sentence-transformers". The author would advise either "all-MiniLM-L6-v2" for English documents or "paraphrase-multilingual-MiniLM-L12-v2" for multi-lingual documents or any other language. [Search](https://huggingface.co/models?pipeline_tag=summarization&sort=downloads&search=multi) for "multi" with tag "summarization in huggingface, then you would get huge models. A [mT5](https://huggingface.co/csebuetnlp/mT5_multilingual_XLSum) model is very large, size upto 2.33GB

Keywords-image pairs can be used for CLIP model training.

#### [watson based video maker](https://github.com/talesdsp/video-maker)

It first downloads wikipedia content from algorithmia, then uses regex to filter out unwanted parts, uses watson AI for sentence cutting, set a limit for max sentences (notice: not summarization), then search image with keywords, finally create video.

In [another similar project](https://github.com/maykbrito/automatic-video-creator/blob/b37d93651e016ac3f8a0731289d84764802c7afc/robots/input/trends.js) IMDB (Popular Film/TV series) and Google search trends (as RSS) are included.

#### [Auto-Editor](https://github.com/WyattBlue/auto-editor)

By passing `--edit` option, you can remove unwanted parts identified by motion or audio (can be combined). It can import clip with manual "cut-out". It can export as json.

#### [Pictory](https://pictory.ai/)

Leveraging 3 millions of tagged video clips and audio, choosing most semantically similar clip to current scene (by extracting keyword -> search images -> compare images to video sources with all embedding things going under the hood (CLIP)), map video word by word to the timeline (to create extractive highlights and remove unwanted words like "um")

#### [Wisecut](https://www.wisecut.video)

Short videos can attract your viewers and converting them into followers (to view more of your long videos). [Make short videos](https://www.wisecut.video/post/leverage-short-videos-to-grow-your-audience) with music, subtitles and facial recognition auto-reframe (detect main speaker). It match the right BGM with the type of content, with audio ducking, which can be achieved with ffmpeg or editly.

It is listed among an [AI marketing tools list](https://github.com/mhmmyu/awesomeAI), which mentions copywriting, social media/email/blog marketing text/content generation (like [copy.ai](https://copy.ai)), text to video

#### [Jumpcutter](https://github.com/potato3d/jumpcutter)

An audio-slience based video cutter. In `jumpcut_file.py` it chops audio into chunks and decide if it is slience or not. The core logic is to first compare max volume of each chunk against threshold, then check in neighbors of every chunk if all of them are slient and cut them out. It has audio speed changing methods from [audiotsm](https://pypi.org/project/audiotsm/).

In [another implementation](https://github.com/madsbacha/jumpcut/blob/master/jumpcut.py), it uses ring buffer by `collections.deque` and applies VAD (Voice Activity Detetion) by [webrtcvad](https://pypi.org/project/webrtcvad/) to every chunk of audio.

#### [Gifcurry](https://github.com/lettier/gifcurry)

Adding text to video, has typing effects, written in haskell. You can add `-m` flag to export video instead of GIF.

#### [Backgroundremover](https://github.com/nadermx/backgroundremover)

A commandline tool powered by torch, removing background from images and video

#### [Moviepy](https://github.com/Zulko/moviepy) most loved commandline video editor?

There are some [cool text effects](https://zulko.github.io/moviepy/examples/moving_letters.html) called "Text with moving letters" (PPT-like), and a [dancing video generator](https://zulko.github.io/moviepy/examples/dancing_knights.html) based on tempo finder and video loop maker, which can help you adjust video speed according to video period and music bpm. The [Star-Wars Text Effect](https://zulko.github.io/moviepy/examples/star_worms.html) reminds me of easing functions used with page scrolling.

### Data collect/analyze

Social media statistics are time series data which should be collected regularly and predictable with time forcasting models.

#### [open-sir](https://github.com/open-sir/open-sir)

Use sirx over sir.

I think it is hard to use. Many "presumed" parameters are out there. It can fit "reproduction rate" but no individual "alpha" and "beta" values.

In tradirional SIR models, beta is infection rate, gamma is recovery rate. While in open-sir it is different. alpha now is beta, beta now is gamma.

#### [Youtube Viral Video Machine Learning Analysis](https://github.com/gdemos01/yttresearch-machine-learning-algorithms-analysis)

Refer to this [document](https://github.com/gdemos01/yttresearch-machine-learning-algorithms-analysis/blob/master/Documentation/Thesis.pdf) for details in data collection and machine learning methods.

Usage:

You can decide whether to copy a video or not when it is posted for only a few days.

Dataset creation:

Monitoring video right at the time it is posted, monitor for a few days, calculate features, then wait for a month or two (it must stablize then), judge the video is viral or not by view counts.

Using multiple machine learning techniques, there are some top features matters the most for viral video forecasting (though you can derive your own by collecting more data (like the follower-view theory if applied), and beware if your video all sucks, you may not get an accurate model out of your data alone):

| Rank | Feature Name | Importance|
|---|---|---|
| 1                  | views_acc | 12%|
| 2                  | views_1 | 11%|
| 3                  | ageRatioReviews_1 | 9%   |
| 4                  | video_duration| 9%  |
| 5                  | comments_1| 5%|
| 6                  | channel_uploads|5%|
| 7                  | ageRatioLikes_1 | 4%|
| 8                  | comments_acc | 4% |
| 9                  | channel_views| 4% |
| 10                 | comments_sentiment_compound |3%|

#### [ViralCaster](https://github.com/jjbreen/ViralCaster)

[TitleParser.py](https://github.com/jjbreen/ViralCaster/blob/master/TitleParser.py) analyses views along with words, getting the most "popular" word or word combinations. It has demo data. It generates "max" "min" "mean" views related to single word or word combinations.

#### [Predictube](https://github.com/dubstack/Predictube)

[peak_detection.py](https://github.com/dubstack/Predictube/blob/master/predictube/analyze/peak_detection/peak_detection.py) use daily view count to categorize and identify trends. "MonoIncr" might be our desired category.

#### [Video Viralization Tool](https://github.com/FilipePires98/VideoViralizationTool)

It uses relative infection ratio instead of absolute to predict the trend. By "information cascade" it means statistics can be used to predict future view counts. It considers individuals and viewers as nodes. It suggests different relationships between parameters in SIR model and data (likes, shares, comments, new subscribers, subscribers, length, quality, tag keywords, description keywords).
