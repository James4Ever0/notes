edit `/etc/systemd/resolved.conf` then run:

```bash
systemctl restart systemd-resolved
systemctl enable systemd-resolved
mv /etc/resolv.conf /etc/resolv.conf.bak
ln -s /run/systemd/resolve/resolv.conf /etc
```