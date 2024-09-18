---
title: Setup RAID5 on LVM
created: 2024-09-12T08:12:46+00:00
modified: 2024-09-18T10:32:52+08:00
---

# Setup RAID5

LVM GUI:

https://www.linuxjournal.com/content/review-gui-lvm-tools

---

It is best that you simulate the whole process on a virtual machine, with six 1GB disks attached.

Disable IO thread, use native async IO, and disable SSD emulation.

---

To permanently delete an RAID array `/dev/md0` presumeably on `/dev/sd[bdefg]`, you need to run the following script:

```bash
umount /dev/md0
mdadm --stop /dev/md0
wipefs -f -a /dev/sd[bcdefg]
```

---

No matter you partition individual RAID member disks or not, you always have a different filesystem UUID than the RAID UUID. The filesystem UUID is different if you reformat the disk. To mount the filesystem using `/etc/fstab`, you need to specify the filesystem UUID. Alternatively, use the device path like `/dev/md/<hostname>:<md_number>` or `/dev/md<dynamic_number>`.

---

To create a five disk RAID5 array plus one hot spare disk ranging from `/dev/sd[bcdefg]` all with identical size, do the following:

```bash
wipefs -a -f /dev/sd[bcdefg]
mdadm --create --level=5 --raid-devices=5 /dev/sd[bcdef] --spare-devices=1 /dev/sdg
mkfs.ext4 /dev/md0
# after this step you need to collect the filesystem UUIDf within the command output, or from the output below
lsblk -o UUID,NAME
```

And append the following line to `/etc/fstab`, then reboot.

```bash
UUID=<filesystem_uuid> /mnt/<mountpoint_name> ext4 nofail 0 2
```

If you want to create a RAID array across different disks with different sizes, make sure the larger physical disks each have one smaller partition with size identical to the smallest physical disk.

To partition a disk, run the following commands:

```bash
wipefs -a -f /dev/sd<disk_letter>
fdisk /dev/sd<disk_letter>
# type: g Enter n Enter Enter Enter w Enter 
# if you want to specify the partition size, type something other than default after 'n'
```
