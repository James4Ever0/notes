---
title: motion vector estimation, motion vector export, ffmpeg advanced usage
created: 2022-09-11T23:44:52+08:00
modified: 2022-09-13T02:20:37+08:00
---

# motion verctor estimation, motion vector export, ffmpeg advanced usage

## use cases

to detect hard-coded subtitles, crop the region and detect sudden changes

can also use pyscenedetect to do the job

## pyav

[docs](https://pyav.org/docs/stable/)

```bash 
pip3 install av
```

## remove/detect silence

 ... silencedetect     A->A       Detect silence.
 ... silenceremove     A->A       Remove silence.

## frame interpolate

```bash
ffmpeg -y -i "/root/Desktop/works/pyjom/tests/random_giphy_gifs/samoyed.gif" \
 -vf "minterpolate,scale=w=iw*2:h=ih*2:flags=lanczos,hqdn3d" \
 -r 60 ffmpeg_samoyed.mp4
```

## motion estimation

to get mosaic motion vectors and visualize:

```bash
ffmpeg -i "/root/Desktop/works/pyjom/tests/random_giphy_gifs/samoyed.gif" \
 -vf "mestimate=epzs:mb_size=16:search_param=7, codecview=mv=pf+bf+bb"  \
 mestimate_output.mp4 -y
```

## get help
### on specific filter:
```bash
ffmpeg -h filter=showspectrumpic
```
### on all filters:
```bash
ffmpeg -filters
```

## crop detection, picture in picture (PIP) detection

```bash
ffmpeg -i "/root/Desktop/works/pyjom/samples/video/LiEIfnsvn.mp4" \
-vf "mestimate,cropdetect=mode=mvedges,metadata=mode=print" \
-f null -
```

## [scene change detection](https://brontosaurusrex.github.io/2019/03/11/ffmpeg-scene-detection/)

```bash
ffmpeg -hide_banner -i "$file" -an \
-filter:v \
"select='gt(scene,0.2)',showinfo" \
-f null \
- 2>&1
```

## extract motion vectors

ffmpeg can produce motion vector estimation but it is not exportable, only for internal use.

mp4 format provides motion vector information thus maybe we need not to use GPU to get those 'optical flow' data.

### extract by using ffmpeg apis

[mv-extractor](https://github.com/LukasBommes/mv-extractor) Extract frames and motion vectors from H.264 and MPEG-4 encoded video.

### extract from mp4 file

[mpegflow](https://github.com/vadimkantorov/mpegflow) for easy extraction of motion vectors stored in video files

[mv-tractus](https://github.com/jishnujayakumar/MV-Tractus): A simple tool to extract motion vectors from h264 encoded videos.

## [take screenshot at time:](https://write.corbpie.com/taking-screenshot-with-ffmpeg/#:~:text=To%20take%20a%20screenshot%20or%20save%20a%20frame,means%20the%20frame%20number%20at%20the%20time%20specified.)
```bash
ffmpeg -ss 01:10:35 -i invideo.mp4 -vframes 1 -q:v 3 screenshot.jpg

```

## video denoise filters:
dctdnoiz fftdnoiz hqdn3d nlmeans owdenoise removegrain vaguedenoiser nlmeans_opencl yaepblur

## super-resolution, resampling:

### deeplearning model, tensorflow
```bash
env LD_LIBRARY_PATH=/root/anaconda3/pkgs/cudatoolkit-10.0.130-0/lib/:/root/anaconda3/pkgs/cudnn-7.6.5-cuda10.0_0/lib/:$LD_LIBRARY_PATH \
ffmpeg -i "/root/Desktop/works/pyjom/samples/video/LiEIfnsvn.mp4" \
-y -vf \
"sr=dnn_backend=tensorflow:model=./sr/espcn.pb,yaepblur" \
 supertest.mp4
```

### use standard scale method:
```bash
ffmpeg -y -i "/root/Desktop/works/pyjom/tests/random_giphy_gifs/samoyed.gif"\
 -vf "minterpolate,scale=w=iw*2:h=ih*2:flags=lanczos,hqdn3d" \
 -r 60 ffmpeg_samoyed.mp4
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
