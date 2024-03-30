---
title: 'Hacker virtual machines, containers'
created: '2024-03-30T02:56:14.947Z'
modified: '2024-03-30T04:02:11.284Z'
---

# Hacker virtual machines, containers

on termux you use [`proot-distro`](https://github.com/termux/proot-distro) for installing kali and blackarch linux.

install via  `apt install proot-distro`

---

use podman over docker, since we do not need gpu here.

---

parrot linux also has docker images.

---

on ubuntu you use docker for pulling [kali](https://www.kali.org/docs/containers/official-kalilinux-docker-images/) and [blackarch](https://github.com/BlackArch/blackarch-docker) linux images. latest images are pushed to docker hub.

```bash
sudo docker pull kalilinux/kali-rolling 
# kali-rolling does not contain all packages
# run inside container: apt update && apt install -y kali-linux-headless

sudo docker pull blackarchlinux/blackarch
```

---

it is always recommend to update and upgrade the blackarch you installed.
