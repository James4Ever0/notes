---
title: Route network interface to specific application
created: '2024-06-03T06:30:04.514Z'
modified: '2024-06-03T07:30:11.362Z'
---

# Route network interface to specific application

It is not advised to do so with dual wifi connection. Have not tested with ethernet and wifi dual connection.

---

Use `firejail`

```bash
sudo firejail --net=wlan0 --ip=dhcp --noprofile <program cmd>
```

---

Use `dante` and `proxychains-ng`

```bash
sudo apt install dante-server proxychains-ng
```

Create a user for proxy login:

```bash
sudo useradd -r -s /usr/bin/false proxy
sudo passwd proxy # set it as proxy_password
```

Now edit the `dante` config file at `/etc/dante.conf`:

```
internal: eth0 port = 1080
external: wlan0
socksmethod: username

user.privileged: proxy
user.unprivileged: nobody
user.libwrap: nobody

client pass {
    from: 0.0.0.0/0 to: 0.0.0.0/0
}

socks pass {
    from: 0.0.0.0/0 to: 0.0.0.0/0
}
```

Find the `[ProxyList]` section and add the following line in `/etc/proxychains.conf`:

```
socks5 127.0.0.1 1080 proxy proxy_password
```

Run the program with proxychains-ng:

```bash
proxychains <program cmd>
```
