---
created: 2024-07-24T13:56:14+08:00
modified: 2024-07-25T14:22:27+08:00
---

# k8s reboot pod and vm

to reboot you need to kill the pod/vmi and recreate it, thereby all its states will be lost.

```bash
kubectl delete pod <pod_name>
kubectl delete vmi <vmi_name>
```

for vmi there is an option called `soft-reboot` which is absent in pods. however the vm runner pod must not exit.

```bash
virtctl soft-reboot <vmi_name>
```

for pod you you can scale down the replicaset of deployment (recommended), or kill the pod directly.

for vm you are supposed to use `virtctl`
