---
title: PM2 daemonize any app
created: '2024-07-08T08:59:45.000Z'
modified: '2024-09-08T15:05:43.845Z'
---

# PM2 daemonize any app

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
