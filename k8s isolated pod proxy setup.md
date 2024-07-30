---
created: 2024-07-24T07:55:49+08:00
modified: 2024-07-30T16:45:57+08:00
---

# k8s isolated pod proxy setup

you need to disable intranet access with `NetworkPolicy`

find more info about intranet ranges here:

https://github.com/langgenius/dify/blob/main/docker/ssrf_proxy/squid.conf.template

http://www.squid-cache.org/Doc/config/acl/

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-intranet-egress
spec:
  podSelector:
    matchLabels:
      app: hello-world
  policyTypes:
    - Egress
  egress:
    - to:
        - ipBlock:
            cidr: ::/0
            except:
              - fc00::/7
              - fe80::/10
        - ipBlock:
            cidr: 0.0.0.0/0
            except:
              - 0.0.0.0/8
              - 10.0.0.0/8
              - 100.64.0.0/10
              - 169.254.0.0/16
              - 172.16.0.0/12
              - 192.168.0.0/16
```

if you do not want to use `tun` routing and rely on application specific proxy adaptors, you can `export` environment variables at:

- `/etc/profile` or `/etc/profile.d/proxy.sh`
- `~/.bashrc`

---

use clash tun mode by `config.yaml`

```yaml
interface-name: en0 # 与 `tun.auto-detect-interface` 冲突

tun:
  enable: true
  stack: system # or gvisor
  # dns-hijack:
  #   - 8.8.8.8:53
  #   - tcp://8.8.8.8:53
  #   - any:53
  #   - tcp://any:53
  auto-route: true # manage `ip route` and `ip rules`
  auto-redir: true # manage nftable REDIRECT
  auto-detect-interface: true # 与 `interface-name` 冲突
```

ref:

https://clash.wiki/premium/tun-device.html

---

by the most you would create a `tun` device, then route all traffic to the device after you have installed necessary softwares.

```bash
ip tuntap add mode tun dev tun0
ip addr add 198.18.0.1/15 dev tun0
ip link set dev tun0 up

# download tun2socks
# https://github.com/xjasonlyu/tun2socks
```

you need to use the default gateway otherwise you will not be able to reach the dns.

the default gateway will differ from nodes. it is recommended to fetch it from `ip route`

for ubuntu containers you would run `apt install iproute2` first

```bash
DNS_IP=8.8.8.8

GATEWAY_IP=$(ip route | grep default | grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b")

DEFAULT_ROUTE=$(ip route | grep default | sed -E 's/( metric.*)?$/ metric 100/g;')

DEFAULT_NET_DEVICE=$(ip route | grep default | grep -oP '(?<=dev )\w+')

# run with root privilege
ip route delete default

ip route add $DEFAULT_ROUTE

ip route add default dev via 198.18.0.1 tun0
ip route add $DNS_IP via $GATEWAY_IP dev $DEFAULT_NET_DEVICE
```

then launch `tun2socks`

```bash
./tun2socks -interface $DEFAULT_NET_DEVICE -device tun://tun0 -proxy <proxy_protocol>://<proxy_address>
```

to disable the tun network you can run:

```bash
ip route delete default dev tun0
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
