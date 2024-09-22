---
title: TrueNAS tips
created: '2024-09-20T08:15:34.000Z'
modified: '2024-09-22T07:26:25.546Z'
---

# TrueNAS tips

You can add different vdevs as read/write cache in pool settings.

It is safe to add a read-cache device only. Write-cache need to use SLC SSD to ensure integrity when power loss occurs.

---
TrueNAS SCALE needs to be installed on IDE disks.

To create a SAMBA share you need to create a dataset with SMB preset, and a separate account with SAMBA access permission.

Remember to turn the service on (a blue switch to the left of the startup checkbox) while enabling it on boot.

If you cannot load NAS disks in PVE, try to lessen permissions.
