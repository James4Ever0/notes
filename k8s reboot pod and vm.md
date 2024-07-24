---
created: 2024-07-24T13:56:14+08:00
modified: 2024-07-24T19:01:38+08:00
---

# k8s reboot pod and vm

to reboot you need to kill the pod/vmi and recreate it, thereby all its states will be lost.

for vmi there is an option called `soft-reboot` which is absent in pods. however the vm runner pod must not exit.

for pod you you can scale down the replicaset of deployment (recommended), or kill the pod directly.

for vm you are supposed to use `virtctl`
