---
created: 2024-10-12T17:58:23+08:00
modified: 2024-10-12T18:06:14+08:00
---

# Change network interface metric

Metric represents connection cost. Higher metric value means less preferred.

To change metric you can use `nmcli` or `ifmetric`.

```bash
ifmetric <if_name> <metric>

nmcli con mod <conn_name> ipv4.route-metric <metric>

systemctl restart NetworkManager
```
