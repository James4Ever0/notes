---
tags: [find file, locate file, macos, tips]
title: MacOS locate fix and alternative
created: '2022-08-07T05:34:18.266Z'
modified: '2022-08-18T15:29:47.800Z'
---

# MacOS locate fix and alternative

## the fix

to enable the service:
```bash
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist
```
to update locate db:
```bash
sudo /usr/libexec/locate.updatedb
```
or, more conveniently:
```bash
sudo ln -s /usr/libexec/locate.updatedb /usr/local/sbin/updatedb
sudo updatedb
```

## alternative

use `mdfind`
