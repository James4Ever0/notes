---
tags: [host discovery, remote control, service, system manage]
title: the kali command on macos
created: '2022-08-11T16:16:47.656Z'
modified: '2022-08-27T15:28:54.152Z'
---

# the kali command on macos

## debugging

when kali is off, this mac will go crazy and hang everything.

need to scan for kali existance on demand, not all the time.

## developing

should we use p2p networks to speed up remote connections like `n2n` or `tinc`?

would it be interesting to run all our kali connectors ranged from vscode-ssh-connect, rclone mount and direct ssh connection via `kali` command dynamically by our kali discovery service, if we can reload the nginx daemon on demand.

using redis to store some daemon reported values.

how about we set the workding directory of `redis-server` to `/tmp` so that the `dump.rdb` file will never take space after reboot?

we need to know if this will successifully launch after reboot since `/tmp` may not exist by that time

default redis server port: 6379

install redis-server service:
```bash
easyd -w /tmp -l redis_server -- /opt/homebrew/bin/redis-server
```

first value is `online`.

next value is `kali_ip`.

using both value to determine whether to connect to kali or not, and the exact address.

