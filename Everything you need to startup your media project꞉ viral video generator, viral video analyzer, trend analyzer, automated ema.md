---
title: 'Everything you need to startup your media project: viral video generator, viral video analyzer, trend analyzer, automated email account registration, download only a portion of video, peek video screenshots'
created: '2023-01-09T03:22:12.000Z'
modified: '2023-01-12T00:48:10.474Z'
---

# Everything you need to startup your media project: viral video generator, viral video analyzer, trend analyzer, automated email account registration, download only a portion of video, peek video screenshots

收集大up主的名字 根据提取出来的名词 清除文案中的含有名字的句子

for information cascade, treat recommendation system as your target data, and fit your content into the prediction of "to-view" video of popular videos

分析弹幕关键词是否与大量其他视频标题相重合

B站撞车搬运检测：

通过B站搜索Weibo Tumblr Tiktok Youtube的视频ID，可以找出视频是否被转载

通过搜索其他网站的前缀 比如`https://www.youtube.com` 可以得到被转载视频的链接 但是感觉数据不是很靠谱 不是很火的那种 要看大流量的还是得爬首页推荐链接 根据话题搜索

## Viral videos

### Data analyzers

#### [番茄数据](https://www.tomatodata.cn/news/1355.html)

番茄数据提供了从近24小时--近90天B站的最新热门视频，你既可以通过“搜索标题、简介、标签、评论出现关键词”，也可以通过行业分类、播放数、点赞数、投币数、视频时长、观众画像等高级条件，精准定位想要查找领域的热门视频。传播指数的计算方法有待研究。传播指数是根据UP主的粉丝数、视频点赞数、播放数、投币数、分析数等分析出来的综合得分。根据评论热词分析视频观众热点，根据评论用户分析用户画像。

### Video collectors

#### [botTuber: a instagram compilation reposter to youtube](https://github.com/sam5epi0l/BotTuber)

Using `instaloader` and `instalooter`, it can download videos from instagram. It merges a series of video and add intro and outro. It only contains one default title starts with "TRY NOT TO LAUGH" in its "auto" mode.

#### [reddit hot videos to youtube](https://github.com/spantheslayer/yt-upload-automation)

In "TiktokCringe" reddit channel, we are able to get hot posts and video links prefixed by `https://v.redd.it` (from tiktok to reddit) in json format: `https://www.reddit.com/r/TikTokCringe/hot.json?limit=12`. This link looks like some API or subscription. Maybe Bilibili and other sites have similar "hot" json urls. The way to extract video links is in [atmt.sh](https://github.com/spantheslayer/yt-upload-automation/blob/main/atmt.sh). It adds transitions to every video clip.

### Video editors

#### [Auto-Editor](https://github.com/WyattBlue/auto-editor)

By passing `--edit` option, you can remove unwanted parts identified by motion or audio (can be combined). It can import clip with manual "cut-out". It can export as json.

#### [Pictory](https://pictory.ai/)

Leveraging 3 millions of tagged video clips and audio, choosing most semantically similar clip to current scene (by extracting keyword -> search images -> compare images to video sources with all embedding things going under the hood (CLIP)), map video word by word to the timeline (to create extractive highlights and remove unwanted words like "um")

#### [Wisecut](https://www.wisecut.video)

Short videos can attract your viewers and converting them into followers (to view more of your long videos). [Make short videos](https://www.wisecut.video/post/leverage-short-videos-to-grow-your-audience) with music, subtitles and facial recognition auto-reframe (detect main speaker). It match the right BGM with the type of content, with audio ducking.

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

####
