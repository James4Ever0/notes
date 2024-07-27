---
title: k3s change data storage path
created: '2024-07-27T14:25:43.128Z'
modified: '2024-07-27T15:01:46.800Z'
---

# k3s change data storage path

first, stop all k3s services

```bash
# run with root
systemctl stop k3s # k3s-agent otherwise
k3s-killall.sh
```

then modify the service file under `/etc/systemd/system/k3s.service` or `/etc/systemd/system/k3s-agent.service`
