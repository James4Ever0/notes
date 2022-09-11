---
title: 'motion verctor estimation, motion vector export, ffmpeg advanced usage'
created: '2022-09-11T15:44:52.749Z'
modified: '2022-09-11T17:20:35.088Z'
---

# motion verctor estimation, motion vector export, ffmpeg advanced usage

ffmpeg can produce motion vector estimation but it is not exportable, only for internal use.

mp4 format provides motion vector information thus maybe we need not to use GPU to get those 'optical flow' data.

[take screenshot at time:](https://write.corbpie.com/taking-screenshot-with-ffmpeg/#:~:text=To%20take%20a%20screenshot%20or%20save%20a%20frame,means%20the%20frame%20number%20at%20the%20time%20specified.)
```bash
ffmpeg -ss 01:10:35 -i invideo.mp4 -vframes 1 -q:v 3 screenshot.jpg

```

video denoise filters:
dctdnoiz fftdnoiz hqdn3d nlmeans owdenoise removegrain
