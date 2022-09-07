---
title: vapoursynth 光流算法 补帧
created: '2022-09-07T03:59:21.000Z'
modified: '2022-09-07T04:39:31.803Z'
---

# vapoursynth 光流算法 补帧

补帧算法可适用于我们的动态水印追踪系统 但是可能需要优化 才能做到比较快速的补帧 因为水印所在位置的区间实际上只是白色的 不需要过于复杂的网络 同时这种补出来的水印需要逐帧处理 或者两帧一处理 生成的区间数量会非常的多

[python opencv 光流算法详解](https://learnopencv.com/optical-flow-in-opencv/) 分为sparse和dense两种 某种程度上都可以计算场景的变换激烈程度

[vapoursynth get started (official doc)](http://www.vapoursynth.com/doc/gettingstarted.html)

[vapoursynth plugin database](http://vsdb.top/)

[VSRepo plugin manager](https://github.com/vapoursynth/vsrepo) installing vapoursynth plugin via commandline tool 
