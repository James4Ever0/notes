---
title: 'Run GUI programs under cron, monitor root filesystem disk usage and send alarm'
created: '2024-06-19T06:26:15.190Z'
modified: '2024-06-19T06:32:43.635Z'
---

# Run GUI programs under cron, monitor root filesystem disk usage and send alarm

the ultimate solution:

copy all current user environment variables to crontab.

---

to run `notify-send` you have to set `DBUS_SESSION_BUS_ADDRESS`

---

to run other gui programs you set `DISPLAY` and `XAUTHORITY`

---

`wall` works for `tmux` and ssh sessions but not `gnome-terminal`. 

---

script for monitoring disk usage:

```bash
#!/bin/bash

# Get the numerical root filesystem available percentage using df and awk
percentage=$(df / | awk 'NR==2 {sub(/%/, "", $5); print $5}')

# Compare the percentage with the number 10
if [ "$percentage" -gt 10 ]; then
    wall alarm
else
	  wall false_alarm
fi


```

