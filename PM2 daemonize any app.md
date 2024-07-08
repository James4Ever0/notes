---
created: 2024-07-08T16:59:45+08:00
modified: 2024-07-08T17:02:24+08:00
---

# PM2 daemonize any app

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
pm2 monit
pm2 logs
pm2 ls
```
