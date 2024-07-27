---
title: k3s change data storage path
created: '2024-07-27T14:25:43.128Z'
modified: '2024-07-27T15:07:21.606Z'
---

# k3s change data storage path

first, stop all k3s services

```bash
# run with root
systemctl stop k3s # k3s-agent otherwise
k3s-killall.sh
```

copy the legacy data to new location

```bash
rsync -avh --progress /var/lib/rancher/k3s <path_to_store_data>
```

then modify the service file under `/etc/systemd/system/k3s.service` or `/etc/systemd/system/k3s-agent.service`, add one additional flag `--data-dir <path_to_store_data>` to the commandline

restart the service after done

```bash
systemctl daemon-reload
systemctl start k3s
```
