---
created: 2024-07-19T13:34:50+08:00
modified: 2024-07-20T00:12:13+08:00
---

# install microk8s

```bash
sudo snap install --classic microk8s
sudo microk8s enable dns:<dns_ip>
```

config files are at `/var/snap/microk8s/current`, and you need to replace all `docker.io` with some docker mirror to prevent init errors.

run `microk8s inspect` to get errors like hostname casing, and missing file like `/var/snap/microk8s/current/var/kubernetes/backend/localnode.yaml`

---

k3s mirror

```bash
curl -sfL https://rancher-mirror.rancher.cn/k3s/k3s-install.sh | INSTALL_K3S_MIRROR=cn sh -​
```
