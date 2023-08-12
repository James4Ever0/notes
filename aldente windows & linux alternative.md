---
title: aldente windows & linux alternative
created: '2023-08-07T13:41:02.482Z'
modified: '2023-08-12T14:47:11.828Z'
---

# aldente windows & linux alternative

to prevent damage to computer battery due to overcharging

## Linux

kernel 5.5 or newer:

```bash
echo 60 | sudo tee /sys/class/power_supply/BAT0/charge_control_end_threshold
```

For ThinkPads and selected other laptops [tlp](https://linrunner.de/tlp) (acts like powertop which turns off usb devices, so be careful when running long-term programs) provides a unified way
 to configure charge thresholds and recalibrate the battery.


## Windows
