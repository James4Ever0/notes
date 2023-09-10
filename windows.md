---
tags: [backup, stub, time machine]
title: Time Machine Alternative for linux/windows
created: '2022-08-10T08:12:46.237Z'
modified: '2023-09-10T11:20:19.305Z'
---

# Time Machine Alternative for linux/windows

use `test` to check existance some manual created identity file to prove if the endpoint is connected

(really? does that check work for offline rclone samba drives?)

----

format the backup disk as xfs so we can do symlink on it (linux).

----

use `flock` (from `util-linux`) to prevent multiple backup instances from running.

alternative: [run-one](https://blog.dustinkirkland.com/2011/02/introducing-run-one-and-run-this-one.html)

```bash
sudo apt-add-repository ppa:run-one/ppa
sudo apt-get update
sudo apt-get install run-one
```

----

[linux-timemachine](https://github.com/cytopia/linux-timemachine#star-features) supports windows, linux, macOS, using rsync as backend, can use hardlink to make backup management very easy. can delete previous backup without losing data. need external controller to make "circular" or to only keep most recent backups on disk.

[curated list of alternative time machine for OSes other than macOS](https://alternativeto.net/software/time-machine/?platform=linux&p=2)

[timeshift gui backup/restore tool for linux](https://alternativeto.net/software/timeshift/about/)

[duplicity incremental backup](https://duplicity.gitlab.io/) can store backup into encrypted tar files and support IMAP protocol as remote file server


