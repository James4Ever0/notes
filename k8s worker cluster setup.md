---
created: 2024-07-24T10:28:58+08:00
modified: 2024-07-25T18:39:14+08:00
---

# k8s worker cluster setup

k3s has different ways to form a cluster than `kubeadm join`.

https://docs.k3s.io/quick-start

k3s specifies the init command in `/etc/systemd/system/k3s.service`. (`k3s-agent.service` if installed as agent) usually it is `k3s server`.

you need to change it to `k3s agent` in order to join the master node, or pass additional environment variables `K3S_URL=https://<node_ip>:6443` and `K3S_TOKEN=<node-token>` while running k3s installation script.

the node token is at `/var/lib/rancher/k3s/server/node-token`

the agent node still needs to configure registry mirrors at `/etc/rancher/k3s/registries.yaml` for successfully pulling images

---

[k3sup](https://github.com/alexellis/k3sup) can automatically install k3s cluster using ssh connection
