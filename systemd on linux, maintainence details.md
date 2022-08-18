---
tags: [linux, service, system manage, systemd]
title: 'systemd on linux, maintainence details'
created: '2022-08-09T05:51:57.121Z'
modified: '2022-08-18T07:38:56.055Z'
---

# systemd on linux, maintainence details

## view full logs

```bash
journalctl -u <serviceName>.service
```

## create, install, restart, reload

```bash
cd /etc/systemd/system
create <serviceName>.service
systemctl enable <serviceName>.service
systemctl daemon-reload
systemctl start <serviceName>.service
```

## sample systemd service config files

maybe we should add some autorestart configs at it?

frpc_service.service
```js
[Unit]
Description=frpc service, expose ssh, webdav and code-server ports
Wants=network.target
After=syslog.target network-online.target

[Service]
Type=simple
User=root
ExecStart=/root/frp_client_linux/frp_0.36.2_linux_amd64/frpc -c frpc.ini
WorkingDirectory=/root/frp_client_linux/frp_0.36.2_linux_amd64
Restart=on-failure
RestartSec=10
KillMode=process

[Install]
WantedBy=multi-user.target
```

pyjom_webdav_rclone_service.service
```js
[Unit]
Description=rclone webdav served on pyjom, after the disk is mounted

[Service]
User=root
ExecStart=/usr/bin/python3 mount_help_and_serve_pyjom.py
WorkingDirectory=/root/Desktop/works/restore_sessions

[Install]
WantedBy=multi-user.target
```

tempthrottle.service
```js
[Unit]
Description=temperature control, cpu temperature under 60 celsius

[Service]
User=root
ExecStart=/usr/bin/python3 tempthrottle_daemon.py
WorkingDirectory=/root/Desktop/works/restore_sessions

[Install]
WantedBy=multi-user.target

```

clash_fastgithub.service

```js
[Unit]
Description=Clash Fastgithub Proxy
After=network.target

[Service]
Type=simple
Restart=always
ExecStart=/usr/bin/clash -d /etc/clash

[Install]
WantedBy=multi-user.target

```

tujia_scraper_qq_bot.service
```js
[Unit]
Description=two crucial services: tujia scraper, qq bot
Wants=network.target
After=syslog.target network-online.target

[Service]
Environment="DISPLAY=:1"
Environment="XAUTHORITY=/root/.Xauthority"
User=root
ExecStart=/usr/bin/python3 main_daemon.py
WorkingDirectory=/root/Desktop/works/restore_sessions

[Install]
WantedBy=graphical.target

```

sync_git_repos_syncdog.service
```js

[Unit]
Description=syncdog (server), to sync things to the cloud (github)
Wants=sshd.service
Wants=network.target

[Service]
User=root
ExecStart=/usr/bin/python3 syncdog_test.py
WorkingDirectory=/root/Desktop/works/sync_git_repos

[Install]
WantedBy=multi-user.target
```
