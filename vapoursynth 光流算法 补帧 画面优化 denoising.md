---
title: vapoursynth 光流算法 补帧 画面优化 denoising
created: '2022-09-07T03:59:21.000Z'
modified: '2022-09-18T14:26:24.834Z'
---

# vapoursynth 光流算法 补帧 画面优化 denoising

[DBmbk](https://github.com/kewenyu/DBmbk) for easier bezier curve generation

[ffmpeg super resolution filter](https://ffmpeg.org/ffmpeg-filters.html#sr) could get faster if run on gpu with [libtensorflow](https://www.tensorflow.org/install/lang_c)

[VESPCN: real-time super resolution](https://github.com/HighVoltageRocknRoll/sr)

[mpv](https://github.com/stax76/mpv.net) is a media player with VapourSynth built-in, and that's probably how vapoursynth gets in my mac via brew dependency manager

[view.py](https://github.com/UniversalAl/view) is Python module for vapoursynth scripts that previews clips

[to use opencv functions with vapoursynth](https://github.com/WolframRhodium/muvsfunc/wiki/OpenCV-Python-for-VapourSynth)

svp is [free on linux](https://www.svp-team.com/zh/get/#), offering [plugin for vlc](https://www.svp-team.com/wiki/SVP:VLC#Using_SVP_in_VLC) while vlc cannot be run as root

you might harvest some prebuilt binaries of vapoursynth plugins for linux

补帧算法可适用于我们的动态水印追踪系统 但是可能需要优化 才能做到比较快速的补帧 因为水印所在位置的区间实际上只是白色的 不需要过于复杂的网络 同时这种补出来的水印需要逐帧处理 或者两帧一处理 生成的区间数量会非常的多

it is much easier to do this on windows since we need quick evaluation. might run this on virtualbox?

[build scripts](https://github.com/Bl4Cc4t/homebrew-vsplugins/tree/master/Formula) on how to build plugins for macos, including how to configure the installation prefix.

brew compatible, macos compatible vapoursynth plugin build script provider: [homebrew-vsplugins](https://github.com/Bl4Cc4t/homebrew-vsplugins) does not provide build scripts for all plugins avaliable for windows, and it requires [additional linking](https://github.com/Bl4Cc4t/homebrew-vsplugins/blob/master/linkvsp.sh)

[tutorial](https://forum.doom9.org/showthread.php?t=175522) on how to configure it: (is it intel only?)

Alternative VapourSynth Install Method (Brew):
IMPORTANT: Brew users will need to create and set the autoload folder prior to installing VapourSynth! Simply run the following commands:
Code:

```bash
mkdir -p /usr/local/lib/vapoursynth
mkdir -p "$HOME/Library/Application Support/VapourSynth"
touch "$HOME/Library/Application Support/VapourSynth/vapoursynth.conf"
echo UserPluginDir=/usr/local/lib/vapoursynth >> "$HOME/Library/Application Support/VapourSynth/vapoursynth.conf"
echo SystemPluginDir=/usr/local/lib/vapoursynth >> "$HOME/Library/Application Support/VapourSynth/vapoursynth.conf"
```
(Optional) Create desktop shortcuts for the plugins and scripts folders. Run the following commands in terminal:
Code:
```bash
mkdir $HOME/Desktop/VapourSynth
ln -s /usr/local/lib/vapoursynth $HOME/Desktop/VapourSynth/Plugins
ln -s /usr/local/lib/python3.9/site-packages $HOME/Desktop/VapourSynth/Scripts
```
Use brew command:
Code:
```bash
brew install vapoursynth

```

[bm3d denoising using cuda](https://github.com/WolframRhodium/VapourSynth-BM3DCUDA)

[fft3d denoising](https://vsdb.top/plugins/fft3dfilter)

[python opencv 光流算法详解](https://learnopencv.com/optical-flow-in-opencv/) 分为sparse和dense两种 某种程度上都可以计算场景的变换激烈程度

[frame interpolation using deep optical flow](https://github.com/vineeths96/Video-Interpolation-using-Deep-Optical-Flow)

[openmmlab mmflow](https://github.com/open-mmlab/mmflow)

[google research: FILM (frame interpolation for large motion)](https://github.com/google-research/frame-interpolation)

[vapoursynth get started (official doc)](http://www.vapoursynth.com/doc/gettingstarted.html)

[vapoursynth plugin database](http://vsdb.top/) only provide prebuilt binaries for windows while the plugin source code might work with linux and macos (if it has the source code)

[VSRepo plugin manager](https://github.com/vapoursynth/vsrepo) installing vapoursynth plugin via commandline tool and vsrepo is only supported on windows, for other platforms we need to compile plugins manually. 

[nazorip vapoursynth blogs](https://www.nazorip.site/category/Tutorials/)

[nazorip bezier curve](https://nazorip.site/archives/32/)

[nazorip gamma curve and convolution](https://nazorip.site/archives/56/)

[flowpy: tool for visualizing and processing image with optical flow](https://nazorip.site/archives/56/)
