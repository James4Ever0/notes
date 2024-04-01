---
title: 'Hacker virtual machines, containers'
created: '2024-03-30T02:56:14.947Z'
modified: '2024-04-01T06:03:52.266Z'
---

# Hacker virtual machines, containers

on termux you use [`proot-distro`](https://github.com/termux/proot-distro) for installing kali and blackarch linux.

install via  `apt install proot-distro`

---

use podman over docker, since we do not need gpu here, and want faster pulling speed.

recent version of podman requires extra layer of domain/index specification before searching and pulling images.

```bash
podman search docker.io/kali
podman pull docker.io/kalilinux/kali-rolling
```

---

if you want to run network scanning commands like `nmap`, you would grant the container sufficient permissions:

```bash
podman run --cap-add=NET_RAW --cap-add=NET_ADMIN --rm -it docker.io/parrotsec/security
```


---

[metasploitable2](https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide/), [parrot linux](https://parrotsec.org/docs/cloud/parrot-on-docker/) also have docker images. more cybersecurity/ctf related images to be found.

run this query in search engines:
```
site:github.com cybersecurity docker images
```

https://github.com/VaultSEC/osint
https://github.com/PberAcademy/Dockerimages

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
