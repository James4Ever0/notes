---
tags: [driver, hardware, HID, stylus, tablet]
title: Letsketch libwacom
created: '2022-05-06T11:59:22.000Z'
modified: '2022-08-18T15:30:10.642Z'
---

# Letsketch libwacom

working on archlinux arm:
libwacom 2.1.0-1

not working on kali linux:
libwacom-bin 2.2.0-1

full reference:

https://github.com/DIGImend/digimend-kernel-drivers/issues/514

sudo nano /etc/X11/xorg.conf

Section "InputClass"
Identifier "Tablet"
Driver "wacom"
MatchDevicePath "/dev/input/event*"
MatchUSBID "6161:4d15"
EndSection

to debug input problems:

https://wiki.ubuntu.com/DebuggingMouseDetection#:~:text=In%20case%20your%20mouse%20stops%20working%20after%20a,your%20mouse%20stops%20working.%20...%20More%20items...%20

check /etc/logs/Xorg.0.logs
