---
title: Use Tesla GPU in WDDM mode on Windows
created: '2024-03-25T02:38:13.514Z'
modified: '2024-03-25T02:41:41.792Z'
---

# Use Tesla GPU in WDDM mode on Windows

On Linux there is no difference between WDDM and TCC.

On Windows, all Tesla GPUs operate at TCC mode, which cannot utilize functions like DirectML, Vulkan etc.

To enable WDDM mode, you need to change the registry.

The path: `Computer\HKEY`

```

```

Run:

```cmd
nvidia-smi -g -dm 0
```

Make sure to select the right GPU when using Vulkan.
