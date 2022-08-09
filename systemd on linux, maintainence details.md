---
title: 'systemd on linux, maintainence details'
created: '2022-08-09T05:51:57.121Z'
modified: '2022-08-09T05:59:52.063Z'
---

# systemd on linux, maintainence details

## view full logs

```bash

```

## create, install, restart, reload

```bash
cd /etc/systemd/system
create <serviceName>.service
systemctl enable <serviceName>.service
systemctl daemon-reload
systemctl start <serviceName>.service
```
