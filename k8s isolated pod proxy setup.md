---
created: 2024-07-24T07:55:49+08:00
modified: 2024-07-24T18:52:20+08:00
---

# k8s isolated pod proxy setup

by the most you would create a `tun` device, then route all traffic to the device after you have installed necessary softwares.

you need to use the default gateway `10.42.0.1` otherwise you will not be able to reach the dns.

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
