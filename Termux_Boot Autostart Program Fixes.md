---
tags: [autostart, stub, termux]
title: Termux_Boot Autostart Program Fixes
created: '2022-08-06T18:38:53.000Z'
modified: '2022-08-18T16:04:13.417Z'
---

# Termux:Boot Autostart Program Fixes

according to [this](https://github.com/termux/termux-boot/issues/58), termux:boot on android 10 and above will not work. instead, change all executables with relative paths in init scripts to their absolute paths. if any referred executable is a script file containing other executable with non-absolute paths(except for those built-in programs like am), change that too.

mostly we hold wakelock, start sshd, crond or nginx and other non-blocking, non-interactive apps at start.
