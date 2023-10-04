---
title: cpu/gpu temperature monitor
created: '2023-10-04T15:07:51.646Z'
modified: '2023-10-04T15:10:59.478Z'
---

# cpu/gpu temperature monitor

we've got [archey4](https://github.com/HorlogeSkynet/archey4), a cross-platform sysinfo gather tool

## macos

[osx-core-temp]() for old intel macs

[]() and [smctemp](https://github.com/narugit/smctemp) for m1 and newer macs


place this under `` to run archey4 with cpu temperature:
```bash
#!/bin/bash
smctemp -c

```

## windows

coretemp

## linux

psensor
