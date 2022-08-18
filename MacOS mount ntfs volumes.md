---
tags: [macos, ntfs, system manage, tips, usage]
title: MacOS mount ntfs volumes
created: '2022-08-08T05:19:14.354Z'
modified: '2022-08-18T15:36:54.872Z'
---

# MacOS mount ntfs volumes

macos mount ntfs read-only by default.

code from [mounty.app](https://mounty.app/)

mounty is somehow not working so manual remount is needed.

one needs to click the remount button to mount it again under `/Users/jamesbrown/.mounty/Toshiba3000`

```bash
sudo umount /Volumes/Toshiba3000
sudo mkdir /Volumes/Toshiba3000; sudo mount -t ntfs -o rw,auto,nobrowse /dev/<diskIdentifier> /Volumes/Toshiba3000
```
