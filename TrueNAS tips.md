---
created: 2024-09-20T16:15:34+08:00
modified: 2024-09-20T16:56:00+08:00
---

# TrueNAS tips

TrueNAS SCALE needs to be installed on IDE disks.

To create a SAMBA share you need to create a dataset with SMB preset, and a separate account with SAMBA access permission.

Remember to turn the service on (a blue switch to the left of the startup checkbox) while enabling it on boot.

If you cannot load NAS disks in PVE, try to lessen permissions.
