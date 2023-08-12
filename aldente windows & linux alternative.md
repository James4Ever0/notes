---
title: aldente windows & linux alternative
created: '2023-08-07T13:41:02.482Z'
modified: '2023-08-12T13:43:36.735Z'
---

# aldente windows & linux alternative

to prevent damage to computer battery due to overcharging

## Linux

```bash
echo 60 | sudo tee /sys/class/power_supply/BAT0/charge_control_end_threshold
```

## Windows
