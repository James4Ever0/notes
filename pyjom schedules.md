---
tags: [pyjom, schedule]
title: pyjom schedules
created: '2022-08-17T19:02:54.000Z'
modified: '2022-08-21T18:05:37.767Z'
---

# pyjom dev schedules

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
- [ ] bgm somehow not in sync (too broad bpm/clip ranges?)
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
- [ ] do not remove subtitle and crop active region (reviewer's resource not used? but i rather advise you to do it directly since it requires less computational power)
- [ ] do not have minimum motion threshold (reviewer's fault? also recommend you to do this in producer)
-----------------
- [ ] remove all watermarks, subtitles and crop video boundaries accordingly
- [ ] source video and audio, improve highlight algorithm
- [ ] generate appropriate title, cover, info and tags
- [ ] collect feedback after the post
- [ ] find some shocking fonts for cover and subtitle, english and chinese
- [x] make that karaoke effect/beautify the lyrics
- [ ] make lyrics sync logic fluent, according to what have learned from karaoke effects
- [ ] make selected video clips fluent, no abrupt cuts, maybe we need pyscenedetect?

## text to video, template based video generator
- [ ] analyze danmaku
- [ ] cut the crap and understand each clip's meaning
- [ ] process the video clips
- [ ] process the audio clips
- [ ] remove all hints that may lead to copyright issues

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
