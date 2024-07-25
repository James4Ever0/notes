---
created: 2024-07-24T07:55:49+08:00
modified: 2024-07-25T15:43:55+08:00
---

# k8s isolated pod proxy setup

by the most you would create a `tun` device, then route all traffic to the device after you have installed necessary softwares.

you need to use the default gateway otherwise you will not be able to reach the dns.

the default gateway will differ from nodes. it is recommended to fetch it from `ip route`

```bash
DNS_IP=8.8.8.8

GATEWAY_IP=$(ip route | grep default | grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b")

DEFAULT_ROUTE=$(ip route | grep default | sed -E 's/( metric.*)?$/ metric 100/g;')

DEFAULT_NET_DEVICE=$(ip route | grep default | grep -oP '(?<=dev )\w+')

# run with root privilege
ip route delete default

ip route add $DEFAULT_ROUTE

ip route add default dev tun0
ip route add $DNS_IP via $GATEWAY_IP dev $DEFAULT_NET_DEVICE
```

you need to configure the `dnsPolicy` to `None` in manifest otherwise it would add the cluster dns ip to `/etc/resolv.conf`, slowing down the lookup process and making it very hard to change during the runtime.

not every domain shall be reached via public proxies, unless it is graranteed to not be discovered by the gfw.

the full network isolation scheme can be shown below:

```
            internet interface
                    |
intranet-isolated proxy server (hysteria)
                    |
cluster service with clusterIP
                    |
isolated socks5 server with only access
 to the hysteria service clusterIP and port
                    |
local socks5 service with clusterIP
                    |
isolated tun-routed pod with only access 
 to socks5 service clusterIP and port

```