---
title: proxmox cluster setup
created: '2024-07-27T17:30:03.108Z'
modified: '2024-07-27T17:33:45.304Z'
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

https://www.howtoforge.com/tutorial/how-to-configure-a-proxmox-ve-4-multi-node-cluster/

https://pve.proxmox.com/wiki/Cluster_Manager
