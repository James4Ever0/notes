---
title: proxy.py forward localhost proxy to public ip address
created: '2023-02-13T06:51:19.585Z'
modified: '2023-02-13T06:53:47.705Z'
---

# proxy.py forward localhost proxy to public ip address

say if you only have one such proxy on localhost, not exposed on router: `localhost:8981`

you execute the command, using `proxy.py`:

```bash

proxy -\
    --plugins proxy.plugin.ProxyPoolPlugin \
    --proxy-pool localhost:8981

```
