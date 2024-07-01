---
title: Block unauthorized access by firewall
created: '2024-07-01T09:57:20.993Z'
modified: '2024-07-01T09:58:40.738Z'
---

# Block unauthorized access by firewall

use `ufw`

```bash
sudo ufw deny from <ip_range> port <port>
```

`firewalld`

```bash
sudo firewall-cmd 
```
