---
title: k3s change data storage path
created: '2024-07-27T14:25:43.128Z'
modified: '2024-07-27T14:27:34.722Z'
---

# k3s change data storage path

first, stop all k3s services

```
# run with root
systemctl stop k3s # k3s-agent otherwise
k3s-killall.sh
```
