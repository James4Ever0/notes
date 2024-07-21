---
created: 2024-07-21T21:03:07+08:00
modified: 2024-07-21T21:11:16+08:00
---

# k8s python api library

install the official library with `pip install kubernetes`

---

the default api config path for k8s is at `~/.kube/config`

`k3s` is at `/etc/rancher/k3s/k3s.yaml`

`microk8s` is at `/var/snap/microk8s/current/credentials/kubelet.config`

you can also set `KUBECONFIG` environment variable to let `kubernetes` python library know where the config is

---

to use it:

```bash
from kubernetes import client, config

# Configs can be set in Configuration class directly or using helper utility

config_path = ...
config.load_kube_config(config_path)

v1 = client.CoreV1Api()
print("Listing pods with their IPs:")
ret = v1.list_pod_for_all_namespaces(watch=False)
for i in ret.items:
    print("%s\t%s\t%s" % (i.status.pod_ip, i.metadata.namespace, i.metadata.name))
```
