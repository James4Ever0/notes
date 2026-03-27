---
created: 2026-03-27T11:19:50+08:00
modified: 2026-03-27T11:21:54+08:00
---

# adbfs

we want su support, so we can read and write across all file systems.

an easier alternative might be running ssh server in termux, then use sshfs to mount its file system instead.

https://deepwiki.com/zach-klippenstein/adbfs

sudo apt update
sudo apt install python3-fuse

pip install fuse-python

https://github.com/spion/adbfs-rootless
