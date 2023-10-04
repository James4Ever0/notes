---
title: cpu/gpu temperature monitor
created: '2023-10-04T15:07:51.646Z'
modified: '2023-10-04T15:15:06.019Z'
---

# cpu/gpu temperature monitor

we've got [archey4](https://github.com/HorlogeSkynet/archey4), a cross-platform sysinfo gather tool, with info on temperature monitor tools

## macos

[osx-core-temp](https://github.com/lavoiesl/osx-cpu-temp) for old intel macs

[apple_sensors](https://github.com/fermion-star/apple_sensors/) and [smctemp](https://github.com/narugit/smctemp) for m1 and newer macs

place this under `/opt/homebrew/bin/osx-cpu-temp` to run archey4 with cpu temperature:

```bash
#!/bin/bash
smctemp -c
```

## windows

[coretemp](https://www.alcpu.com/CoreTemp/)

## linux

[psensor](https://github.com/chinf/psensor)
