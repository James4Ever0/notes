---
created: 2024-07-24T13:56:14+08:00
modified: 2024-07-25T14:27:52+08:00
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

for pod you you can scale down the replicas of deployment (recommended), or kill the pod directly.

```bash
kubectl scale deployment <deployment_name> --replicas=0
kubectl scale deployment <deployment_name> --replicas=<original replica num>
```

for vm you are supposed to use `virtctl`

```bash
virtctl start <vm_name>
virtctl stop <vm_name>
virtctl restart <vm_name>
```
