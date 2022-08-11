---
title: 'Copy Symlink itself to change pyjom''s location, install easyd services for macos local pyjom watchdog'
created: '2022-08-11T06:41:13.000Z'
modified: '2022-08-11T09:47:44.367Z'
---

# Copy Symlink itself to change pyjom's location, install easyd services for macos local pyjom watchdog

```bash
cd /media/root/parrot
cp -R -P /media/root/help1/pyjom .
```

because of the qqChatBot task, pyjom on kali may be syncing too often. need to check the watchdog logs.

install macos pyjom watchdog (local):

```bash
easyd -l pyjom_local_watchdog -w /Users/jamesbrown/Desktop/works/sync_git_repos -- /usr/bin/python3 /Users/jamesbrown/Desktop/works/sync_git_repos/watchdog_macos.py
```

install macos pyjom syncdog (local):

```bash
easyd -l pyjom_local_syncdog -w /Users/jamesbrown/Desktop/works/sync_git_repos -- /usr/bin/python3 /Users/jamesbrown/Desktop/works/sync_git_repos/syncdog_macos.py
```
