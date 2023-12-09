---
title: How to fix OpenCL platform not found issue on android
created: '2023-12-09T12:09:24.148Z'
modified: '2023-12-09T12:13:13.525Z'
---

# How to fix OpenCL platform not found issue on android

To run `llama.cpp` on Oneplus Ace2V, you need an extra step:

```bash
export LD_LIBRARY_PATH=/vendor/lib64:/vendor/lib64/mt6983:/vendor/lib64/egl/mt6983
```
