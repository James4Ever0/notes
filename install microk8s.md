---
created: 2024-07-19T13:34:50+08:00
modified: 2024-07-19T18:47:27+08:00
---

# install microk8s

```bash
sudo snap install --classic microk8s
sudo microk8s enable dns:<dns_ip>
```

config files are at `/var/snap/microk8s/current`, and you need to replace all `docker.io` with some docker mirror to prevent init errors.
