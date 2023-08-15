---
tags: [backup, stub, time machine]
title: Time Machine Alternative for linux/windows
created: '2022-08-10T08:12:46.237Z'
modified: '2023-08-15T00:07:21.597Z'
---

# Time Machine Alternative for linux/windows

use `flock` to prevent multiple backup instances from running.

----

[linux-timemachine](https://github.com/cytopia/linux-timemachine#star-features) supports windows, linux, macOS, using rsync as backend, can use hardlink to make backup management very easy. can delete previous backup without losing data. need external controller to make "circular" or to only keep most recent backups on disk.

[curated list of alternative time machine for OSes other than macOS](https://alternativeto.net/software/time-machine/?platform=linux&p=2)

[timeshift gui backup/restore tool for linux](https://alternativeto.net/software/timeshift/about/)

[duplicity incremental backup](https://duplicity.gitlab.io/) can store backup into encrypted tar files and support IMAP protocol as remote file server


