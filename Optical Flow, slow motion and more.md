---
created: 2022-04-19T16:50:32+08:00
modified: 2022-04-19T16:56:10+08:00
---

# Optical Flow, slow motion and more

https://github.com/slowmoVideo/slowmoVideo

it uses gpu and optical flow to do frame interpolation.

able to do instance segmentation if the optical flow boundary is clear and continuous.

build opencv with opencv_contrib and -DWITH_CUDA=ON to enable cudaoptflow.
