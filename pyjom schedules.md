---
tags: [pyjom, schedule]
title: pyjom schedules
created: 2022-08-18T03:02:54+08:00
modified: 2022-09-10T19:17:53+08:00
---

# pyjom dev schedules

## 整活
- [ ] 应 急 诈 骗 食 品 (派蒙加Rick Ashley 如何混合？）

## recommendation
- [ ] use txtai to do NLU and recommend things to people

## topic discovery/acquiring
### trending topics
- [ ] baidu search trending
- [ ] sogou trending
- [ ] bilibili trending
- [ ] wechat trending
- [ ] toutiao trending
- [ ] tencent trending
- [ ] netease trending
- [ ] youtube trending
- [ ] reddit trending
- [ ] twitch trending
### popular topics
- [ ] baijiahao popular topics
- [ ] bilibili popular topics
- [ ] douyin popular topics
### personal/customized topics
- [ ] tencent qq customized (can associate with mail)
- [ ] wechat customized
- [ ] bilibili per user customized

## dog/cat video generation
### make render engine runnable
issues:
- [x] video length too long (10 mins)
it was the speed calculation error.
- [x] bgm somehow not in sync (too broad bpm/clip ranges?)
- [ ] to analyze the peaks (abrupt changes) in bgm and grab louder peaks using `pyloudnorm` (getting audio volume)
```bash
pip3 install pyloudnorm
```

```python
import soundfile as sf
import pyloudnorm as pyln

data, rate = sf.read("0055014.wav") # load audio (with shape (samples, channels))
print(data.shape)
meter = pyln.Meter(rate) # create BS.1770 meter
loudness = meter.integrated_loudness(data) # measure loudness
print(loudness)
```
- [ ] place video on loudest points, abrupt changes detected by talib or just take direvative and gaussian average
- [ ] video too repetitive (small corpus?)
- [x] do not remove subtitle and crop active region (reviewer's resource not used? but i rather advise you to do it directly since it requires less computational power)
- [ ] do not have minimum motion threshold (reviewer's fault? also recommend you to do this in producer)
-----------------
- [x] remove all watermarks, subtitles and crop video boundaries accordingly
- [ ] source video and audio (infinite, basic test is to find 500 sources at once without duplicate, second test is to find 500 second is to find 500 without duplicate twice), improve highlight algorithm
- [ ] find 500 songs without duplicate at once
- [ ] find 500 songs no duplicate twice
- [ ] find 500 animal videos without duplicate
- [ ] find 500 animal videos no duplicate twice
- [ ] generate appropriate title, cover, info and tags
- [ ] collect feedback after the post
- [ ] find some shocking fonts for cover and subtitle, english and chinese
- [x] make that karaoke effect
- [x] make ass with karaoke effect with lrc files
- [x] make lyrics sync logic fluent, according to what have learned from karaoke effects
- [ ] make selected video clips fluent, no abrupt cuts, maybe we need pyscenedetect?

## text to video, template based video generator (this is perhaps the most complex video generator ever. do it with caution, it might also includes the flipcard, narrator and slideshow based generators)
### generator models subarchitecture (subcategories of template based generators)
#### flipcard
#### slideshow (video and audio, might also include the dog&cat video!)
#### narrator
#### summarized video
________________________
### policy evasion, NSFW filters
- [ ] remove all hints from image, video, audio and script that may lead to copyright issues
________________________
### analyze the media content and metadata, relationships
- [ ] analyze danmaku
- [ ] paraphrase the script
- [ ] cut the crap and understand each clip's meaning
________________________

### process the video clips, like changing the human figure, changing face, stylish the video, adding 2d to 3d effects
________________________

### process the audio clips, like changing voice, adding sound effects, separating audio/music tracks, ducking
________________________

### index, retrieve and align video and audio content according to our collected database
________________________

### retrieve and align video and audio according to our smart search agent (keyword extractor, related words) and do live compilation
________________________

## qq managing
- [ ] mitm chats in friends
- [ ] mitm chats in groups
- [ ] source and send pictures to qzone
- [ ] source and send pictures to chat
- [ ] reduce posting frequency by group size and feedback
- [ ] post relative video link relative to group topic

## personal info collecting and email/sms bulk sending
- [ ] avoid mail being trashed or turned into junk
- [ ] collect and make mail templates for mail posting

## voice changer
- [ ] vst based voice changer
- [ ] train or find a decent voice generator 御姐音语料库 小受音语料库
请在b站或者qq群里面寻找 或者什么其他的有关的地方寻找 谢谢

## 直播 live streaming
- [ ] source the video
如果是同一个站的 尽量放一个月以前的视频 半个月以前的音频
- [ ] prepare some space for storing live streaming data
- [ ] source the audio
- [ ] automatic interactions
- [ ] handle the vtuber model's actions
