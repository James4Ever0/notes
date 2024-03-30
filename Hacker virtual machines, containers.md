---
title: 'Hacker virtual machines, containers'
created: '2024-03-30T02:56:14.947Z'
modified: '2024-03-30T03:32:20.133Z'
---

# Hacker virtual machines, containers

on termux you use [`proot-distro`](https://github.com/termux/proot-distro) for installing kali and blackarch linux.

install via  `apt install proot-distro`

---

on ubuntu you use docker for pulling [kali](https://www.kali.org/docs/containers/official-kalilinux-docker-images/) and [blackarch](https://github.com/BlackArch/blackarch-docker) linux images. latest images are pushed to docker hub.

```bash
sudo docker pull kalilinux/kali-rolling
sudo docker pull blackarchlinux/blackarch
```

---

it is always recommend to update and upgrade the blackarch you installed.
