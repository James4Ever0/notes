---
title: 'Copy Symlink itself to change pyjom''s location, install easyd services for macos local pyjom watchdog'
created: '2022-08-11T06:41:13.000Z'
modified: '2022-08-11T19:05:15.860Z'
---

# Copy Symlink itself to change pyjom's location, install easyd services for macos local pyjom watchdog

```bash
cd /media/root/parrot
cp -R -P /media/root/help1/pyjom .
```

because of the qqChatBot task, pyjom on kali may be syncing too often. need to check the watchdog logs.

turned out it is the `__pycache__` dirs to be blamed

disable all sync related services on macos for debug:

main issue happens after local vscode launched.

the issue is such that the proxy setting not right.

we need to add some code for it. consider adding that to kali?

```python

```

```bash
launchctl stop gui/501/pyjom_local_watchdog;
launchctl kill TERM gui/501/pyjom_local_watchdog;
launchctl unload gui/501/pyjom_local_watchdog;
launchctl disable gui/501/pyjom_local_watchdog;
launchctl remove gui/501/pyjom_local_watchdog;

launchctl stop gui/501/pyjom_local_syncdog;
launchctl kill TERM gui/501/pyjom_local_syncdog;
launchctl unload gui/501/pyjom_local_syncdog;
launchctl disable gui/501/pyjom_local_syncdog;
launchctl remove gui/501/pyjom_local_syncdog

```

install macos pyjom watchdog (local):

```bash
easyd -l pyjom_local_watchdog -w /Users/jamesbrown/Desktop/works/sync_git_repos -- /usr/bin/python3 /Users/jamesbrown/Desktop/works/sync_git_repos/watchdog_macos.py
```

install macos pyjom syncdog (local):

```bash
easyd -l pyjom_local_syncdog -w /Users/jamesbrown/Desktop/works/sync_git_repos -- /usr/bin/python3 /Users/jamesbrown/Desktop/works/sync_git_repos/syncdog_macos.py
```
