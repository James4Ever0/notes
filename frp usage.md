---
title: frp usage
created: '2024-06-13T02:06:56.411Z'
modified: '2024-06-13T03:42:43.969Z'
---

# frp usage

ssh port must be secured with pubkey only authentication

search for `free frp` or `frp 免费` to get free frp providers

use `masscan` over these servers to find open ports and candidates

```toml
serverAddr = "frp.freefrp.net"
serverPort = 7000
auth.method = "token"
auth.token = "freefrp.net"


```
