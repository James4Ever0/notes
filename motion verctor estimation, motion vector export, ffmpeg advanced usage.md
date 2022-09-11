---
title: 'motion verctor estimation, motion vector export, ffmpeg advanced usage'
created: '2022-09-11T15:44:52.749Z'
modified: '2022-09-11T17:18:14.435Z'
---

# motion verctor estimation, motion vector export, ffmpeg advanced usage

ffmpeg can produce motion vector estimation but it is not exportable, only for internal use.

mp4 format provides motion vector information thus maybe we need not to use GPU to get those 'optical flow' data.

take screenshot at time:
```bash
ffmpeg -ss 01:10:35 -i invideo.mp4 -vframes 1 -q:v 3 screenshot.jpg

```
