---
title: PVE tips
created: 2024-09-08T15:04:23+00:00
modified: 2024-10-15T16:46:30+08:00
---

# PVE tips

https://pve.sqlsec.com

Increase the MTU of both physical network cards and VM network cards to 9000 can cause cluster interaction error.

## Growing an existing partition

use growpart in cloud-utils

## Multi-ethernet and multi-bridge config

If you plug in another ethernet cable while PVE is running, it won't work. Instead you have to set "Autostart" to on, while using `ethtool` to check the link presence.

If you want to have multiple VM bridges, you do not set an IP like xxx.xxx.xxx.0/xx, instead make that zero some other number unoccupied, which will be the IP address of PVE host.

Meanwhile, other VMs may need to manually configure IP addresses and gateway.

## PVE cluster config read-only after removing a node

```bash
pvecm expected 1
```

https://aurlen.net/w/en/proxmox-etc-pve-nodes-node-qemu-server-read-only-after-removing-a-node-from-a-cluster

## VM startup timeout after passing through GPU cards

Try to run this command in `tmux`:

```bash
qm start <vmid> --timeout 0
```

Or configure hugepages:

Add `hugepagez=1GB default_hugepagez=2M` to file `/etc/default/grub`, then run:

```bash
update-grub
```

Then change the VM config:

```bash
qm set <vmid> --hugepages 1024
qm set <vmid> --numa 1
```

https://forum.proxmox.com/threads/vm-start-failed-got-timeout.66361/

https://forum.proxmox.com/threads/one-of-20-kvm-vm-does-not-start-reliably.61011

https://forum.proxmox.com/threads/enable-1gb-hugepages-for-vm-guest.59704

https://forum.proxmox.com/threads/16gb-ram-vm-problem.106388

https://forum.proxmox.com/threads/hugepage-allocation-failed.53092


## Host randomly crashes after passing through a single GPU connected to another GPU using NVLink

Pass two GPUs to the same VM, or neither.

Patch PCI passthrough settings:

## Pass disk to VM

```bash
# you need the disk id to ensure consistency, also do not mount the disk.
qm set <vm_name> -scsi<disk_no> /dev/disk/by-id/<disk_id>
```

https://pve.proxmox.com/wiki/Passthrough_Physical_Disk_to_Virtual_Machine_(VM)

## Setup LVM group

```bash
wipefs -f -a /dev/sd[abcdef]
pvcreate /dev/sd[abcdef]
vgcreate <vg_name> /dev/sd[abcdef]
```

## Import QCOW2 files to PVE

https://getlabsdone.com/how-to-import-qcow2-into-proxmox-server-step-by-step

## Install pvetools

```bash
echo "nameserver 8.8.8.8" >> /etc/resolv.conf && rm -rf pvetools && rm -rf /etc/apt/sources.list.d/pve-enterprise.list && export LC_ALL=en_US.UTF-8 && apt update && apt -y install git && git clone https://github.com/ivanhao/pvetools.git && echo "cd /root/pvetools && ./pvetools.sh" > pvetools/pvetools && chmod +x pvetools/pvetools* && ln -s /root/pvetools/pvetools /usr/local/bin/pvetools && pvetools
```

## Setup a cluster

Make sure there is no TOTP anywhere.

Make sure nodes can ping each other by self-recognized IP addresses.

https://rudimartinsen.com/2024/06/03/proxmox-pve-cluster

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

## Fix Mellanox network card conflicts

Sometimes your default network card will be named differently after plugging in a new Melloanox card, or changing PCIE spliting configurations.

You can either hard-code default network card with MAC address or configure the bridge network with new card name.

If you just want to temporarily fix the issue, do the following:

```bash
systemctl # look for ethernet device names
ip link set up <device_name>
pvesh get /nodes/<node_name>/network
pvesh set /nodes/<node_name>/network/vmbr<bridge_number>
 --type bridge --bridge_ports <device_name>
systemctl restart networking # or reboot if it has no effect
```



https://pve.proxmox.com/wiki/Network_Configuration

## Setup Mellanox intranet connection

PVE has `mlnx-core` driver, and is enough to get 10G ethernet.

First install necessary tools:

```bash
apt update
apt install -y ethtool net-tools
```

Next list all network interfaces:

```bash
ip link
ip link set up <interface_name>
```

Check the suspected network interface:

```bash
ethtool <interface_name> | grep -E 'Speed|Link detected'
```

Now get the names of 10Gb/s and connected interfaces, create two Linux bridge networks on both machines, with IP addresses like `10.128.0.1/24` and `10.128.0.2/24` respectively.

Ping each other and test file transfer:

```bash
# first machine, 10.128.0.1
ping -c 1 10.128.0.1
ping -c 1 10.128.0.2
fallocate -l 20G testfile
python3 -m http.server

# second machine, 10.128.0.2
curl -O http://10.128.0.1:8000/testfile
```

## Setup second network interface in virtual machine

### Ubuntu

Get the network interface name

```bash
ip link
```

Next, edit the file `/etc/network/interfaces`:

```
auto <interface_name>
iface <interface_name> inet static
    address 10.60.0.3
    netmask 255.255.255.0
```

Restart the service

```bash
sudo systemctl restart networking
```
