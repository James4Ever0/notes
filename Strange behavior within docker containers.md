---
title: Strange behavior within docker containers
created: '2024-05-29T02:44:43.717Z'
modified: '2024-05-29T02:49:34.300Z'
---

# Strange behavior within docker containers

Symlinked files are not working properly from the start. Taking `msfconsole` for example, when running container from image `parrotsec/security`, it will get stuck if we immediately execute `msfconsole` once logged in, but we can mitigate the problem by first change into the directory where `msfconsole` really locates, then execute it from there.

```bash
docker run --rm -it parrotsec/security

# it will stuck
msfconsole
# note the following will also stuck
/usr/share/metasploit-framework/msfconsole

# instead let's first change directory
cd /usr/share/metasploit-framework
# then invoke the binary
./msfconsole
```