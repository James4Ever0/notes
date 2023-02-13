---
title: proxy.py forward localhost proxy to public ip address
created: '2023-02-13T06:51:19.585Z'
modified: '2023-02-13T06:54:53.133Z'
---

# proxy.py forward localhost proxy to public ip address

say if you only have one such proxy on localhost, not exposed on router: `localhost:8981`

you execute the command, using [proxy.py](https://pypi.org/project/proxy.py/):

```bash
proxy --port <public_proxy_port> --host <public_proxy_ip_address> \
    --plugins proxy.plugin.ProxyPoolPlugin \
    --proxy-pool localhost:8981
```
