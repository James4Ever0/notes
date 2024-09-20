---
tags: [commandline, emergency, kali, linux, remedy, system manage]
title: Boot into Linux commandline (tty)
created: 2022-05-06T19:03:48+00:00
modified: 2024-09-20T15:01:09+08:00
---

# Boot into Linux commandline (tty)

when xorg fails, one must use commandline to debug problems.

put '3' after the longest line of boot commands.

use ssh to collect logs even if the main interface is stuck somehow (like libinput faliure)

reference:

https://www.linuxandubuntu.com/home/how-to-boot-into-linux-command-line/amp

---

In case you forget the password, press 'e' when you see the grub menu, replace 'ro quite splash' with 'rw init=/bin/bash', then press ctrl+x.

https://linuxconfig.org/recover-reset-forgotten-linux-root-password
