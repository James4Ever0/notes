## method 1

edit `/etc/systemd/resolved.conf` then run:

```bash
systemctl restart systemd-resolved
systemctl enable systemd-resolved
mv /etc/resolv.conf /etc/resolv.conf.bak
ln -s /run/systemd/resolve/resolv.conf /etc
```

## method 2

Install the `resolvconf` package:

```bash
sudo apt-get install resolvconf
```

Edit the `/etc/resolvconf/resolv.conf.d/head` file:

```bash
sudo nano /etc/resolvconf/resolv.conf.d/head
```

Add the DNS servers:

```
nameserver 1.1.1.2
nameserver 1.0.0.2
```

Enable and start the `resolvconf` service:

```bash
sudo systemctl enable --now resolvconf.service
```
