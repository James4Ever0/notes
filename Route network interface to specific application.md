---
title: Route network interface to specific application
created: '2024-06-03T06:30:04.514Z'
modified: '2024-06-03T08:00:25.672Z'
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

Now edit the `dante` config file at `/etc/dante.conf`:

```
internal: eth0 port = 1080
external: wlan0
socksmethod: username

user.privileged: root
user.unprivileged: nobody
user.libwrap: nobody

client pass {
    from: 0.0.0.0/0 to: 0.0.0.0/0
}

socks pass {
    from: 0.0.0.0/0 to: 0.0.0.0/0
}
```

Run the daemon by:

```bash
danted
```

Find the `[ProxyList]` section and add the following line in `/etc/proxychains.conf`:

```
socks5 127.0.0.1 1080 root <root_password>
```

Run the program with proxychains-ng:

```bash
proxychains <program cmd>
```

You can test your configuration like:

```bash
curl -x socks5://root:root@127.0.0.1:1080 https://www.baidu.com
```

If you run `danted` like `systemctl start danted`, you can configure a separate user for authentication. You have to change `/etc/danted.conf` and `/etc/proxychains.conf` accordingly.

```bash
sudo useradd -r -s /bin/false your_dante_user
sudo passwd your_dante_user
```
