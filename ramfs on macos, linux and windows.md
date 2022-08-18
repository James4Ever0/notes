---
tags: [ramfs, system manage]
title: 'ramfs on macos, linux and windows'
created: '2022-08-11T11:28:39.000Z'
modified: '2022-08-18T07:37:31.050Z'
---

# ramfs on macos, linux and windows

## linux

simply use /dev/shm

the only difference is that [ramfs on linux is unbounded while tmpfs is bounded](https://linuxhint.com/create-ramdisk-linux/)

create bounded tmpfs:
```bash
mount -t tmpfs -o size=2g tmpfs /mnt/tmp
```

or yoy labor yourself to mount some additional ramfs:

```bash
mount -t ramfs -o size=2g ramfs /mnt/tmp
```

## macos

/private/tmp is not ramdisk. it is just a directory cleared by startup.

[ram-shell: A simple script to create a in-memory filesystem on macOS](https://github.com/KizzyCode/ramfs-shell)

[RAM-backed filesystem mounter for Mac OS X](https://github.com/srcshelton/ramfs#:~:text=A%20memory-backed%20filesystem%20mounter%20for%20Mac%20OS%20X,not%20survive%20a%20reboot%20or%20even%20being%20unmounted.)

create and mount ramdisk:
```bash
 #!/bin/sh
ramfs_size_mb=2100
mount_point=/tmp/rdisk

mkramdisk() {
  ramfs_size_sectors=$((${ramfs_size_mb}*1024*1024/512))
  ramdisk_dev=`hdid -nomount ram://${ramfs_size_sectors}`

  newfs_hfs -v 'ram disk' ${ramdisk_dev}
  mkdir -p ${mount_point}
  mount -o noatime -t hfs ${ramdisk_dev} ${mount_point}

  echo "remove with:"
  echo "umount ${mount_point}"
  echo "diskutil eject ${ramdisk_dev}"
}
```

[to replace /private/tmp with ramfs and registered as launchd service](https://www.cnblogs.com/emitial/p/ramfs-on-mac.html)

calculate sector numbers by hand:

disk_size(MiB)* 1024KiB/MiB * 1024B/KiB / 512B/sector = #sectors

```bash
hdiutil attach -nomount ram://#sectors
#get returned value afterwards!
newfs_hfs -v 'Ramdisk' <returned_disk_device_id>
# maybe you should create apfs case sensitive instead?

#mount disk
mkdir -p ~/Ramdisk
# may change fs type accordingly when using apfs
mount -o noatime -t hfs <returned_disk_device_id> ~/Ramdisk
```

## windows

[a curated ramdisk software list](https://www.geckoandfly.com/21507/ramdisk-virtual-disk-memory/#:~:text=RAMDisk%20is%20a%20program%20that%20takes%20a%20portion,default%20‘ReadyBoost’%20found%20in%20Microsoft%20Windows%20operating%20system.)

use third-party ramdisk tool like [imdisk](https://sourceforge.net/projects/imdisk-toolkit/), [eram](https://github.com/Zero3K/ERAM) with kernel driver installed, secure boot disabled (no uefi maybe?)
