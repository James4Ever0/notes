---
title: MacOS mount ntfs volumes
created: '2022-08-08T05:19:14.354Z'
modified: '2022-08-08T05:25:26.580Z'
---

# MacOS mount ntfs volumes

macos mount ntfs read-only by default.

code from [mounty.app](https://mounty.app/)

mounty is somehow not working so manual remount is needed.

```bash
sudo umount /Volumes/Toshiba3000
sudo mkdir /Volumes/Toshiba3000; sudo mount -t ntfs -o rw,auto,nobrowse /dev/<diskIdentifier> /Volumes/Toshiba3000
```
