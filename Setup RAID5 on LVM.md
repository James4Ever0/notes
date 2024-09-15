---
title: Setup RAID5 on LVM
created: '2024-09-12T08:12:46.000Z'
modified: '2024-09-15T04:37:58.877Z'
---

# Setup RAID5

LVM GUI:

https://www.linuxjournal.com/content/review-gui-lvm-tools

---

It is best that you simulate the whole process on a virtual machine, with six 1GB disks attached.

Disable IO thread, use native async IO, and disable SSD emulation.

---

No matter you partition individual RAID member disks or not, you always have a different filesystem UUID than the RAID UUID. The filesystem UUID is different if you reformat the disk. To mount the filesystem using `/etc/fstab`, you need to specify the filesystem UUID. Alternatively, use the device path like `/dev/md/<hostname>:<md_number>` or `/dev/md<dynamic_number>`.

---

To create a five disk RAID5 array plus one hot spare disk ranging from `/dev/sd[bcdefg]` all with identical size, do the following:

```bash
wipefs -a -f /dev/sd[bcdefg]
mdadm --create --type raid5
mkfs.ext4 /dev/md0
# after this step you need to collect the filesystem UUID
```

And append the following line to `/etc/fstab`, then reboot.f

If you want to create a RAID array across different disks with different sizes, make sure the larger physical disks each have one smaller partition with size identical to the smallest physical disk.

To partition a disk, run the following commands:

```bash
wipefs -a -f /dev/sd<disk_letter>
fdisk /dev/sd<disk_letter>
# type: g Enter n Enter Enter Enter w Enter 
# if you want to specify the partition size, type something other than default after 'n'
```



