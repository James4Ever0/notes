---
created: 2024-07-26T11:39:40+08:00
modified: 2024-09-08T05:30:30+08:00
---

# Change default IP range settings for network sharing

When use network sharing along with k8s things could go wrong. Ubuntu uses `10.42.0.1/24` which interferes with k8s routing table. It has a larger `metric` value so the network will be shadowed.

To fix it you do not use `ip route` or `ip addr`. You use `nmcli`.

To persist changes you need `nmcli con edit <connection_name>`

https://bytexd.com/how-to-use-the-nmcli-command-to-manage-networkmanager

You need to restart the client machine to get new IP.

---

```bash
nmcli # check all connections
nmcli device modify <shared_device> ipv4.addr <non_conflict_ip_range>
```

Remember to unplug and replug the cable from client side.
