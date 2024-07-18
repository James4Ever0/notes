---
title: amdgpu, rocm and pytorch
created: 2023-10-10T17:13:14+00:00
modified: 2024-07-18T20:44:57+08:00
---

# amdgpu, rocm and pytorch

https://scale-lang.com/

---

rocm is trash to apu. use vulkan or opengl (alternative backends)

---

find latest build in pytorch nightly repo

use sudo before invoking amdgpu related commands, otherwise unavailable

---

use directml (pytorch, tensorflow) instead. need windows.

you need to set the shared graphical memory to a larger value.

rocm does not work for integrated graphic cards (even if you build it and configured the card name), and supported amd cards are limited.
