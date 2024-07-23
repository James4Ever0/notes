---
title: install microk8s
created: 2024-07-19T05:34:50+00:00
modified: 2024-07-23T15:07:57+08:00
---

# install microk8s

network policy:

https://minikube.sigs.k8s.io/docs/handbook/network_policy/

https://docs.tigera.io/calico/latest/network-policy/get-started/calico-policy/calico-network-policy

persistent volume:

https://minikube.sigs.k8s.io/docs/handbook/persistent_volumes/

---

```bash
sudo snap install --classic microk8s
sudo microk8s enable dns:<dns_ip>
```

config files are at `/var/snap/microk8s/current`, and you need to replace all `docker.io` with some docker mirror to prevent init errors.

run `microk8s inspect` to get errors like hostname casing, and missing file like `/var/snap/microk8s/current/var/kubernetes/backend/localnode.yaml`

you need to configure multiple registries for `docker.io` and `registry.k8s.io` under `/var/snap/microk8s/current/args/certs.d`

in order to use some mirror site which does not support `/v2` url, you have to add `override_path = true` in config

mirror sites:

https://github.com/docker-mirrors/website

https://github.com/cmliu/CF-Workers-docker.io/issues/8

https://github.com/kubesre/docker-registry-mirrors

https://github.com/lawrenceching/gitbook/blob/master/docker-repositories-in-china.md

reference:

https://github.com/containerd/containerd/blob/main/docs/hosts.md

https://microk8s.io/docs/registry-private

---

install k3s

```bash
curl -sfL https://get.k3s.io > k3s_setup.sh
# replace the line if GITHUB_URL to some github mirror instead
bash k3s_setup.sh
```

k3s mirror

```bash
curl -sfL https://rancher-mirror.rancher.cn/k3s/k3s-install.sh | INSTALL_K3S_MIRROR=cn sh -​
```

registry config:

https://docs.k3s.io/installation/private-registry

---

k0s install:

https://docs.k0sproject.io/stable/install/

```bash
curl -sSLf https://get.k0s.sh | sudo sh
sudo k0s install controller --single
sudo k0s start
```

config:

https://docs.k0sproject.io/stable/runtime/
