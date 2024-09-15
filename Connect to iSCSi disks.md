---
title: Connect to iSCSi disks
created: '2024-09-12T07:31:22.000Z'
modified: '2024-09-15T05:37:00.127Z'
---

# Connect to iSCSi disks

https://manjaro.site/how-to-connect-to-iscsi-volume-from-ubuntu-20-04

```bash
sudo apt update
sudo apt install open-iscsi
```

Edit the file `/etc/iscsi/initiatorname.conf` with `sudo`

```
InitiatorName <prefix>.org.freenas.ctl
```

Edit `/etc/iscsi/iscsid.conf` with `sudo`:

```

```
