---
created: 2024-07-25T12:14:55+08:00
modified: 2024-07-25T13:04:30+08:00
---

# k8s start pod at specific node

specify `nodeSelector` or `nodeName` in `Pod` or`VirtualMachineInstance` manifest

```bash
kubectl run <pod name> --image=<image name> -it --rm --overrides='{"spec":{"nodeName": "<node name>"}}' -- /bin/sh
```
