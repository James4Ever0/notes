---
title: MacOS mount ntfs volumes
created: '2022-08-08T05:19:14.354Z'
modified: '2022-08-08T05:19:54.542Z'
---

# MacOS mount ntfs volumes

macos mount ntfs read-only by default.

code from [mounty.app]()

```bash
sudo umount /Volumes/UNTITLED
sudo mount -t ntfs -o rw,auto,nobrowse /dev/disk3s1 ~/ntfs-volume
```
