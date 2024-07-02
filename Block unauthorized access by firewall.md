---
title: Block unauthorized access by firewall
created: '2024-07-01T09:57:20.993Z'
modified: '2024-07-02T08:57:49.403Z'
---

# Block unauthorized access by firewall

`ufw`

```bash
sudo ufw deny from <ip_range> port <port>
```

`firewalld`

```bash
sudo firewall-cmd --add-rich-rule='rule family="ipv4" source address="<ip_range>" port protocol="tcp" port="<port>" drop'
```

