---
created: 2024-07-24T10:28:58+08:00
modified: 2024-07-25T10:41:39+08:00
---

# k8s worker cluster setup

k3s has different ways to form a cluster than `kubeadm join`.

k3s specifies the init command in `/etc/systemd/system/k3s.service`. usually it is `k3s server`. you need to change it to `k3s agent` in order to join the master node, or pass additional environment variables `` while running k3s installation script.

the auth token is at `/var/lib/rancher/k3s/server/node-token`

the agent node still needs to configure registry mirrors at `/etc/rancher/k3s/registries.yaml` for successfully pulling images
