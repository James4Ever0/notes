---
title: 'Copy Symlink itself to change pyjom''s location, install easyd services for macos local pyjom watchdog'
created: '2022-08-11T06:41:13.000Z'
modified: '2022-08-11T09:19:15.436Z'
---

# Copy Symlink itself to change pyjom's location, install easyd services for macos local pyjom watchdog

```bash
cd /media/root/parrot
cp -R -P /media/root/help1/pyjom .
```

because of the qqChatBottask, pyjom on kali may be syncing too often.need to check the watchdog logs.

install macos pyjom watchdogs (local):

```bash
easyd -l  -- /opt/homebrew/bin/rclone mount webdav_local_nginx:/ /Volumes/CaseSensitive/pyjom_remote_mountpoint -L
```
