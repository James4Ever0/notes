---
title: PVE tips
created: 2024-09-08T15:04:23+00:00
modified: 2024-09-12T15:48:15+08:00
---

# PVE tips

https://pve.sqlsec.com

## Install pvetools

```bash
echo "nameserver  8.8.8.8" >> /etc/resolv.conf && rm -rf pvetools && rm -rf /etc/apt/sources.list.d/pve-enterprise.list && export LC_ALL=en_US.UTF-8 && apt update && apt -y install git && git clone https://github.com/ivanhao/pvetools.git && echo "cd /root/pvetools && ./pvetools.sh" > pvetools/pvetools && chmod +x pvetools/pvetools* && ln -s /root/pvetools/pvetools /usr/local/bin/pvetools && pvetools
```

## Setting up a cluster

## Make VM to start on boot

## Rename a node

Do not ever do this.

## Setup nested virtualization

You may enable nested virtualization on PVE host with `pvetools`, but you need to tweak VM arguments manually.

Edit the VM config at: ``

Append additional CPU config `vmx` to the config.

https://www.netjue.com/15341.html

## Remove subscription notice

https://johnscs.com/remove-proxmox51-subscription-notice
