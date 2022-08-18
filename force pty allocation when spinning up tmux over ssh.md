---
tags: [pty, ssh, system manage, terminal, tmux]
title: force pty allocation when spinning up tmux over ssh
created: '2022-08-13T06:09:37.706Z'
modified: '2022-08-18T07:41:07.898Z'
---

# force pty allocation when spinning up tmux over ssh

```bash
kali -t tmux attach -t <target_session_name>
```
or:
```bash
kali -o RequestTTY=no tmux attach -t <target_session_name>
```
situation:

```bash
$ ssh 192.0.2.125 tmux attach
open terminal failed: not a terminal
```

The solution is to simply force pseudo-terminal allocation.

```bash
$ ssh -t 192.0.2.125 tmux attach
[...]
```

Define RequestTTY in OpenSSH SSH client configuration file to make this permanent.

```bash
$ cat ~/.ssh/config
Host 192.0.2.125
  RequestTTY yes
```
