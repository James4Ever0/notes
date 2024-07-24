---
created: 2024-07-24T13:56:14+08:00
modified: 2024-07-24T18:54:15+08:00
---

# k8s reboot pod and vm

to reboot you need to kill the pod/vmi and recreate it, thereby all its states will be lost.

for vmi there is an option called `soft-reboot` which is absent in pods.
