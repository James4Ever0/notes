---
title: 'systemd on linux, maintainence details'
created: '2022-08-09T05:51:57.121Z'
modified: '2022-08-09T06:02:43.115Z'
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

pyjom_webdav
```js

```
