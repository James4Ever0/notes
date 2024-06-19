---
title: 'Run GUI programs under cron, monitor root filesystem disk usage and send alarm'
created: '2024-06-19T06:26:15.190Z'
modified: '2024-06-19T06:30:29.882Z'
---

# Run GUI programs under cron, monitor root filesystem disk usage and send alarm

the ultimate solution:

copy all current user environment variables to crontab.

---

to run `notify-send` you have to set `DBUS_SESSION_BUS_ADDRESS`

---

to run other gui programs you set `` and ``

---

`wall` works for `tmux` and ssh sessions but not `gnome-terminal`. 

---

script for monitoring disk usage:

```bash


```

