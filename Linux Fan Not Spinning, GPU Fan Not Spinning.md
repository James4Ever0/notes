---
tags: [fan, hardware, linux, security, system manage, thermal]
title: 'Linux Fan Not Spinning, GPU Fan Not Spinning'
created: '2022-08-11T04:25:28.086Z'
modified: '2022-09-08T19:10:16.161Z'
---

# Linux Fan Not Spinning, GPU Fan Not Spinning

everytime the fucking machine restarts, it fails devastatingly.

the word: `Giving the fans some time to reach full speed...`

hope this shit works?
```bash
echo 255 | sudo tee /sys/class/hwmon/hwmon6/pwm3
echo 255 | sudo tee /sys/class/hwmon/hwmon6/pwm1
```

i have install something other than that. like i8kctl, some thermal controllers by intel (thermald)? but still gpu fan not spinning till now.

```bash
apt install -y lm-sensors fancontrol
sensors-detect
pwmconfig
```
already have cpu frequency under control by running temp_throttle.sh

notes: found controllers `dell_smm-isa-0000`

```bash

Found the following PWM controls:
   hwmon6/pwm1           current value: 255
   hwmon6/pwm3           current value: 255


```

