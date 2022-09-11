---
title: 'motion verctor estimation, motion vector export, ffmpeg advanced usage'
created: '2022-09-11T15:44:52.749Z'
modified: '2022-09-11T17:25:58.945Z'
---

# motion verctor estimation, motion vector export, ffmpeg advanced usage

ffmpeg can produce motion vector estimation but it is not exportable, only for internal use.

mp4 format provides motion vector information thus maybe we need not to use GPU to get those 'optical flow' data.

## [take screenshot at time:](https://write.corbpie.com/taking-screenshot-with-ffmpeg/#:~:text=To%20take%20a%20screenshot%20or%20save%20a%20frame,means%20the%20frame%20number%20at%20the%20time%20specified.)
```bash
ffmpeg -ss 01:10:35 -i invideo.mp4 -vframes 1 -q:v 3 screenshot.jpg

```

## video denoise filters:
dctdnoiz fftdnoiz hqdn3d nlmeans owdenoise removegrain vaguedenoiser nlmeans_opencl yaepblur

## super-resolution, resampling:

### deeplearning model, tensorflow
```bash
env LD_LIBRARY_PATH=/root/anaconda3/pkgs/cudatoolkit-10.0.130-0/lib/:/root/anaconda3/pkgs/cudnn-7.6.5-cuda10.0_0/lib/:$LD_LIBRARY_PATH ffmpeg -i "/root/Desktop/works/pyjom/samples/video/LiEIfnsvn.mp4" -y -vf "sr=dnn_backend=tensorflow:model=./sr/espcn.pb,yaepblur"  supertest.mp4
```

### use standard scale method:
```bash
ffmpeg -y -i "/root/Desktop/works/pyjom/tests/random_giphy_gifs/samoyed.gif" -vf "minterpolate,scale=w=iw*2:h=ih*2:flags=lanczos,hqdn3d" -r 60 ffmpeg_samoyed.mp4
```

### options:

‘fast_bilinear’
Select fast bilinear scaling algorithm.

‘bilinear’
Select bilinear scaling algorithm.

‘bicubic’
Select bicubic scaling algorithm.

‘experimental’
Select experimental scaling algorithm.

‘neighbor’
Select nearest neighbor rescaling algorithm.

‘area’
Select averaging area rescaling algorithm.

‘bicublin’
Select bicubic scaling algorithm for the luma component, bilinear for chroma components.

‘gauss’
Select Gaussian rescaling algorithm.

‘sinc’
Select sinc rescaling algorithm.

‘lanczos’
Select Lanczos rescaling algorithm. The default width (alpha) is 3 and can be changed by setting param0.

‘spline’
Select natural bicubic spline rescaling algorithm.

‘print_info’
Enable printing/debug logging.

‘accurate_rnd’
Enable accurate rounding.

‘full_chroma_int’
Enable full chroma interpolation.

‘full_chroma_inp’
Select full chroma input.

‘bitexact’
Enable bitexact output.
