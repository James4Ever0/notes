---
title: reset windows server password
created: '2023-08-16T15:23:39.539Z'
modified: '2023-08-16T15:25:48.987Z'
---

# reset windows server password

`chntpw` does not work this time. it will auto restore 
the SAM file.

instead, swap `Utilman.exe` (remember to back it up) with `cmd.exe` then click widgets in login window to popup command prompt, type `net user <username> <password>` to reset.


