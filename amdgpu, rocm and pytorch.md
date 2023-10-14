---
title: 'amdgpu, rocm and pytorch'
created: '2023-10-10T17:13:14.000Z'
modified: '2023-10-14T11:48:08.462Z'
---

# amdgpu, rocm and pytorch

rocm is trash to apu. use vulkan or opengl (alternative backends)

---

find latest build in pytorch nightly repo

use sudo before invoking amdgpu related commands, otherwise unavailable

---

use directml (pytorch, tensorflow) instead. need windows.

you need to set the shared graphical memory to a larger value.

rocm does not work for integrated graphic cards (even if you build it and configured the card name), and supported amd cards are limited.


