---
title: proxmox cluster setup
created: '2024-07-27T17:30:03.108Z'
modified: '2024-07-27T17:33:35.748Z'
---

# proxmox cluster setup

either use gui or command line

```bash
# run on master device
pvecm create <cluster_name>
# run on slave device
pvecm add <cluster_ip>
# check on master device
pvecm status
```

reference:


