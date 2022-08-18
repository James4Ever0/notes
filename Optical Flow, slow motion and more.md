---
tags: [slow motion]
title: 'Optical Flow, slow motion and more'
created: '2022-04-19T08:50:32.000Z'
modified: '2022-08-18T14:08:26.587Z'
---

# Optical Flow, slow motion and more

https://github.com/slowmoVideo/slowmoVideo

it uses gpu and optical flow to do frame interpolation.

able to do instance segmentation if the optical flow boundary is clear and continuous.

build opencv with opencv_contrib and -DWITH_CUDA=ON to enable cudaoptflow.
