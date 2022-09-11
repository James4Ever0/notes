---
title: 'motion verctor estimation, motion vector export, ffmpeg advanced usage'
created: '2022-09-11T15:44:52.749Z'
modified: '2022-09-11T17:22:40.973Z'
---

# motion verctor estimation, motion vector export, ffmpeg advanced usage

ffmpeg can produce motion vector estimation but it is not exportable, only for internal use.

mp4 format provides motion vector information thus maybe we need not to use GPU to get those 'optical flow' data.

[take screenshot at time:](https://write.corbpie.com/taking-screenshot-with-ffmpeg/#:~:text=To%20take%20a%20screenshot%20or%20save%20a%20frame,means%20the%20frame%20number%20at%20the%20time%20specified.)
```bash
ffmpeg -ss 01:10:35 -i invideo.mp4 -vframes 1 -q:v 3 screenshot.jpg

```

video denoise filters:
dctdnoiz fftdnoiz hqdn3d nlmeans owdenoise removegrain vaguedenoiser nlmeans_opencl yaepblur

super-resolution, resampling:
```bash
env LD_LIBRARY_PATH=/root/anaconda3/pkgs/cudatoolkit-10.0.130-0/lib/:/root/anaconda3/pkgs/cudnn-7.6.5-cuda10.0_0/lib/:$LD_LIBRARY_PATH ffmpeg -i "/root/Desktop/works/pyjom/samples/video/LiEIfnsvn.mp4" -y -vf "sr=dnn_backend=tensorflow:model=./sr/espcn.pb,yaepblur"  supertest.mp4
```
