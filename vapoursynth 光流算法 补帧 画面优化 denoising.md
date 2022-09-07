---
title: vapoursynth 光流算法 补帧 画面优化 denoising
created: '2022-09-07T03:59:21.000Z'
modified: '2022-09-07T10:26:40.728Z'
---

# vapoursynth 光流算法 补帧 画面优化 denoising

补帧算法可适用于我们的动态水印追踪系统 但是可能需要优化 才能做到比较快速的补帧 因为水印所在位置的区间实际上只是白色的 不需要过于复杂的网络 同时这种补出来的水印需要逐帧处理 或者两帧一处理 生成的区间数量会非常的多

[bm3d denoising using cuda](https://github.com/WolframRhodium/VapourSynth-BM3DCUDA)

[fft3d denoising](https://vsdb.top/plugins/fft3dfilter)

[python opencv 光流算法详解](https://learnopencv.com/optical-flow-in-opencv/) 分为sparse和dense两种 某种程度上都可以计算场景的变换激烈程度

[frame interpolation using deep optical flow](https://github.com/vineeths96/Video-Interpolation-using-Deep-Optical-Flow)

[openmmlab mmflow](https://github.com/open-mmlab/mmflow)

[google research: FILM (frame interpolation for large motion)](https://github.com/google-research/frame-interpolation)

[vapoursynth get started (official doc)](http://www.vapoursynth.com/doc/gettingstarted.html)

[vapoursynth plugin database](http://vsdb.top/)

[VSRepo plugin manager](https://github.com/vapoursynth/vsrepo) installing vapoursynth plugin via commandline tool 

[nazorip vapoursynth blogs](https://www.nazorip.site/category/Tutorials/)

[nazorip bezier curve](https://nazorip.site/archives/32/)

[nazorip gamma curve and convolution](https://nazorip.site/archives/56/)

[flowpy: tool for visualizing and processing image with optical flow](https://nazorip.site/archives/56/)
