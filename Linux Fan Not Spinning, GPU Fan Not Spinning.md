---
tags: [fan, hardware, linux, security, system manage, thermal]
title: 'Linux Fan Not Spinning, GPU Fan Not Spinning'
created: '2022-08-11T04:25:28.086Z'
modified: '2022-08-31T22:35:25.027Z'
---

# Linux Fan Not Spinning, GPU Fan Not Spinning

i have install something other than that. like i8kctl, some thermal controllers by intel (thermald)? but still gpu fan not spinning till now.

```bash
apt install -y lm-sensors fancontrol
sensors-detect
pwmconfig
```
already have cpu frequency under control by running temp_throttle.sh

notes: found controllers `dell-smm
```bash

Found the following PWM controls:
   hwmon6/pwm1           current value: 255
   hwmon6/pwm3           current value: 255


```

