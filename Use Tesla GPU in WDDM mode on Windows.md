---
title: Use Tesla GPU in WDDM mode on Windows
created: '2024-03-25T02:38:13.514Z'
modified: '2024-03-25T02:46:24.184Z'
---

# Use Tesla GPU in WDDM mode on Windows

On Linux there is no difference between WDDM and TCC.

On Windows, all Tesla GPUs operate at TCC mode, which cannot utilize functions like DirectML, Vulkan etc.

To enable WDDM mode, you need to [change the registry](https://blog.csdn.net/qq_45673245/articles/details/128555342).

The path: `Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Class\{4d36e968-e325-11ce-bfc1-08002be10318}`

Find the Tesla card within `000x`, change `AdapterType` to 1, `FeatureScore` to 0xd1, create DWORD `GridLicensedFeatures` to 7, create DWORD `EnableMsHybrid` to 1.

Find the iGPU within `000x`, create DWORD `EnableMsHybrid` to 2.

Restart the computer. When you see the Tesla GPU popping up in Task manager you are all set.

Run:

```cmd
nvidia-smi -g 0 -dm 0
```

Make sure to select the right GPU when using Vulkan.
