---
created: 2024-07-24T10:28:58+08:00
modified: 2024-07-24T18:58:37+08:00
---

# k8s worker cluster setup

k3s has different ways to form a cluster than `kubeadm join`.

k3s specifies the init command in `/etc/systemd/system/k3s.service`. usually it is `k3s server`. you need to change it to `k3s agent` in order to join the master node.
