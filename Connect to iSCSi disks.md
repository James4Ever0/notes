---
title: Connect to iSCSi disks
created: '2024-09-12T07:31:22.000Z'
modified: '2024-09-15T05:43:44.198Z'
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

Edit `/etc/iscsi/iscsid.conf` with `sudo` (if has password):

```
node.session.auth.authmethod = CHAP
node.session.auth.username = username
node.session.auth.password = password
```

Restart services:

```bash
sudo systemctl restart iscsid open-iscsi
```

Join the node:

```bash
sudo iscsiadm -m discovery -t sendtargets -p <portal_ip>
sudo iscsiadm --mode node --targetname <prefix>.org.freenas.ctl:<target_name> --portal <portal_ip> --login
```

To login/logout all targets:

```bash
# login
sudo iscsiadm -m node -l
# logout
sudo iscsiadm -m node -u
```

Now you can view the disk via `sudo fdisk -l`, and use the disk as local physical disks.
