---
created: 2026-07-09T09:09:59+08:00
modified: 2026-07-09T09:14:07+08:00
---

# connect to remote devices securely

using sdk or authed socks5 proxy

because this can ensure the service will not affect other programs running

examples: tailscale, ngrok, zerotier

---

要在Python代码中不依赖系统级Tailscale客户端而直接连接到Tailnet，可以使用官方提供的 tailscale-py 库。它是一个实验性的Python绑定，能让你的应用作为一个独立的节点加入Tailnet。

1. 安装

你可以通过pip直接从PyPI安装：

```bash
pip install tailscale-py
```

2. 核心用法

tailscale-py 是一个异步库，需要与 asyncio 配合使用。以下是一个基础示例，演示如何连接并对指定IP和端口发送UDP消息：

```python
#!/usr/bin/env python3
import asyncio
import tailscale

async def main():
    # 1. 连接到你的 Tailnet
    # 参数1: 用于存储节点状态的文件路径 (会自动创建)
    # 参数2: 你的 Tailscale 认证密钥 (需提前生成)
    dev = await tailscale.connect('tsrs_state.json', "tskey-auth-xxxxx")

    # 2. (可选) 获取本节点在 Tailnet 中的 IPv4 地址
    tailnet_ipv4 = await dev.ipv4_addr()
    print(f"本节点的 Tailnet IP 地址: {tailnet_ipv4}")

    # 3. 在本节点的 Tailnet IP 上绑定一个 UDP 端口
    udp_sock = await dev.udp_bind((tailnet_ipv4, 1234))
    print(f'UDP 绑定成功，本地端点: {udp_sock.local_addr()}')

    # 4. 向 Tailnet 内的一个对端设备发送消息
    #    注意: 替换 '1.2.3.4' 和 5678 为目标设备的 Tailnet IP 和端口
    while True:
        await udp_sock.sendto(('1.2.3.4', 5678), msg=b"HELLO")
        print("消息已发送至对端")
        await asyncio.sleep(1)

if __name__ == "__main__":
    asyncio.run(main())
```

关键概念与注意事项

· 实验性功能：该项目目前处于不稳定阶段，使用时需设置环境变量 TS_RS_EXPERIMENT=this_is_unstable_software。
· 认证密钥：需要提前在Tailscale管理后台生成一个认证密钥（Auth Key），代码中通过 "tskey-auth-xxxxx" 传入。
· 状态文件：'tsrs_state.json' 用于存储节点身份信息，首次运行会自动创建，请确保应用有该路径的读写权限。
· 独立运行：该方式会让你的Python程序作为一个独立节点加入Tailnet，不需要在宿主机上安装或运行Tailscale客户端。

替代方案：管理API

如果你的目标仅仅是查询或管理Tailnet中的设备（例如获取设备列表、监控状态等），而不是作为节点加入网络进行通信，可以考虑使用更成熟的REST API客户端库，如 python-tailscale。这种方式通过API Key与Tailscale的管控平面交互，不涉及建立网络连接。

```python
# 这是一个 API 客户端示例，用于管理而非网络通信
from python-tailscale import Tailscale

client = Tailscale(
    tailnet="your-tailnet-name",
    api_key="tskey-api-xxxxx"
)
# 例如，列出所有设备
devices = client.devices.list()
```

总结

你可以根据具体需求选择方案：

· 若要让Python应用作为独立节点加入Tailnet并进行网络通信，应使用 tailscale-py。
· 若只需要通过API管理或查询Tailnet信息，使用 python-tailscale 等API客户端会更合适。

---

在 Go 语言中，官方推荐的方式是使用 tsnet 包。它和 Python 的 tailscale-py 理念类似，能让你把 Tailscale 节点直接嵌入到 Go 程序里。

核心用法：tsnet 包

tsnet 在进程内部运行一个完全自包含的 Tailscale 节点，使用的是用户态的 TCP/IP 协议栈。这意味着无需系统级守护进程 (tailscaled) 或 root 权限。

最简实现如下（更完整的示例可参考官方“Hello tsnet”教程）：

```go
package main

import (
    "log"
    "net/http"
    "os"

    "tailscale.com/tsnet"
)

func main() {
    // 1. 创建 tsnet Server，配置主机名和认证密钥
    s := &tsnet.Server{
        Hostname: "my-go-service",              // Tailnet 中的设备名[reference:6]
        AuthKey:  os.Getenv("TS_AUTHKEY"),      // 优先从环境变量读取[reference:7]
    }
    defer s.Close()

    // 2. 在 Tailnet 中监听 (Listener 兼容 Go 标准库)[reference:8]
    ln, err := s.Listen("tcp", ":80")
    if err != nil {
        log.Fatal(err)
    }

    // 3. 启动 HTTP 服务 (仅 Tailnet 内可访问)
    log.Fatal(http.Serve(ln, nil))
}
```

认证方式

tsnet.Server 支持多种认证方式，按优先级排序如下：

1. 环境变量：TS_AUTHKEY 或 TS_AUTH_KEY
2. OAuth 客户端密钥：通过 ClientSecret 字段或 TS_CLIENT_SECRET 环境变量
3. 工作负载身份联合：适用于需要无密钥认证的场景

如果没有提供 AuthKey 且节点未注册，首次运行会在日志中打印一个 URL，打开浏览器访问并登录即可完成设备认证。

存储与状态

节点的身份和状态会持久化存储。默认存在用户配置目录下，你也可以通过 Dir 字段自定义路径：

```go
s := &tsnet.Server{
    Hostname: "my-service",
    Dir:      "/path/to/state/directory", // 自定义状态存储目录[reference:16]
}
```

高级特性

· 多节点：一个 Go 程序可运行多个 tsnet.Server 实例，每个实例使用独立的状态目录即可。
· 临时节点：设置 Ephemeral: true，节点断开连接后会自动清理。
· 获取客户端身份：通过 WhoIs 方法可获取连接客户端的用户和节点信息。

备选方案：管理 API

如果只需要进行管理操作（如查询设备列表），可以使用 tailscale.com/client 包来调用 Tailscale 的 Local API 或控制平面 API。

总结

· 若要让 Go 程序作为独立节点加入 Tailnet 并进行网络通信，官方方案是使用 tsnet 包。
· 若只需通过 API 管理或查询 Tailnet 信息，则使用 tailscale.com/client 包更合适。

---

是的，确实存在多个由 tsnet 或 Tailscale 自身支持的 SOCKS5 代理服务。根据你的具体需求，主要有以下几种选择：

· Tailgate
  · 核心特点：一个轻量级的单二进制代理，基于 tsnet 实现，同时支持 SOCKS5 和 HTTP CONNECT 代理，且在同一端口上自动检测协议。
  · 适用场景：需要在无法安装 Tailscale 守护进程的环境（如容器、CI 运行器）中运行代理。
· ts-proxy
  · 核心特点：功能更丰富的用户态 Tailscale 客户端，支持 TCP/UDP 端口转发和 SOCKS5 代理，并且 SOCKS5 代理支持 UDP。
  · 适用场景：需要进行端口转发或需要 UDP 支持的更复杂网络需求。
· SockTail
  · 核心特点：一个极简的二进制文件，加入 Tailnet 并在端口 1080 上暴露本地 SOCKS5 代理。被设计为零配置、无守护进程、无持久化的轻量级工具。
  · 适用场景：寻求临时、快速通道的场景，如红队操作或临时访问。
· TailSocks
  · 核心特点：创建一个本地 SOCKS5 代理服务器，自动将所有流量路由到你选择的 Tailscale 出口节点。
  · 适用场景：希望将特定应用程序的流量通过 Tailscale 网络或特定出口节点路由，而不影响整个系统。
· SockTails
  · 核心特点：一个基于 Tailscale 的 SOCKS5 代理，专为在 Google Cloud Run Jobs 上运行而设计。它作为一个临时节点运行，任务结束后自动从 tailnet 消失。
  · 适用场景：需要在 Google Cloud Run 上按需运行临时代理的场景。
· ts-ssh
  · 核心特点：一个 SSH 客户端，使用 tsnet 连接到 Tailscale 网络。可通过 -D 标志设置 SOCKS5 代理来转发 SSH 隧道中的连接。
  · 适用场景：已经使用 SSH 并希望通过同一隧道获得 SOCKS5 代理功能的场景。

你可以根据自己对功能、持久化和运行环境的需求，从这些项目中选择最合适的一个。
