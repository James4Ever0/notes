---
title: PM2 daemonize any app
created: 2024-07-08T08:59:45+00:00
modified: 2024-10-12T18:05:01+08:00
---

# PM2 daemonize any app

get commandline info by `pm2 info <id>`. you can view them in "script path" and "script args"

---

recover stopped processes by `pm2 resurrect`

---

remember to set unbuffered output flag `-u` before running any python script, otherwise there will be no output in `pm2 log`

---

install and setup pm2 as daemon:

```bash
sudo apt install npm
sudo npm config set registry https://registry.npmmirror.com
sudo npm install -g pm2

pm2 startup
```

run program as daemon:

```bash
pm2 start -n <process_name> <executable_name> -- <process_arguments>

# save all processes
pm2 save

pm2 monit
pm2 logs
pm2 ls
```
