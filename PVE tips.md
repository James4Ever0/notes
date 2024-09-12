---
title: PVE tips
created: 2024-09-08T15:04:23+00:00
modified: 2024-09-12T16:11:55+08:00
---

# PVE tips

https://pve.sqlsec.com

## Install pvetools

```bash
echo "nameserver  8.8.8.8" >> /etc/resolv.conf && rm -rf pvetools && rm -rf /etc/apt/sources.list.d/pve-enterprise.list && export LC_ALL=en_US.UTF-8 && apt update && apt -y install git && git clone https://github.com/ivanhao/pvetools.git && echo "cd /root/pvetools && ./pvetools.sh" > pvetools/pvetools && chmod +x pvetools/pvetools* && ln -s /root/pvetools/pvetools /usr/local/bin/pvetools && pvetools
```

## Setup a cluster

Make sure there is no TOTP anywhere.

Make sure nodes can ping each other by self-recognized IP addresses.

## Migrate to PVE

https://clonezilla.org/

https://pve.proxmox.com/wiki/Advanced_Migration_Techniques_to_Proxmox_VE

## Make VM to start on boot

```bash
qm set <VMID> --onboot 1
```

## Rename a node

Do not ever do this.

## Setup nested virtualization

You may enable nested virtualization on PVE host with `pvetools`, but you need to tweak VM arguments manually.

Edit the VM config at: `/etc/pve/qemu-server/<VMID>.conf`

Append additional CPU config `vmx` to the config.

https://www.netjue.com/15341.html

## Remove subscription notice

You can use `pvetools` to remove the notice, or do it manually below:

https://johnscs.com/remove-proxmox51-subscription-notice
