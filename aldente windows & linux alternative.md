---
title: aldente windows & linux alternative
created: '2023-08-07T13:41:02.000Z'
modified: '2024-03-01T14:47:03.308Z'
---

# aldente windows & linux alternative

to increase stability, you need to prevent computer from overheating (throttle). also, replace normal laptop ram with ecc ram (not server-grade reg-ecc)

but ecc is only supported on Xeon processors.

moreover, you could just use UPS+NUC instead of laptop, to prevent this bloody battery issue.

----

will these charging limits still work if we close the lid? if not, we could possibly damage the battery.

----

to prevent damage to computer battery due to overcharging

## Linux

kernel 5.5 or newer:

```bash
echo 60 | sudo tee /sys/class/power_supply/BAT0/charge_control_end_threshold
```

with [platform-specific drivers](https://unix.stackexchange.com/questions/48534/how-to-adjust-charging-thresholds-of-laptop-battery), look for: `/sys/devices/platform/.*/.*(battery|charge|thresh|limit).*`

For ThinkPads and selected other laptops [tlp](https://linrunner.de/tlp)/tlpui (acts like [powertop](https://01.org/powertop/) which turns off usb devices, so be careful when running long-term programs) provides a unified way
 to configure charge thresholds and recalibrate the battery.

Sometimes tp-smapi from `apt` will not install and you need to fetch the [source]() and compile yourself. Activate the plugin by `sudo modprobe tp_smapi`

Run `sudo systemctl start tlp` to initiate service. Run `sudo tlp- ` to check status.

## Windows
