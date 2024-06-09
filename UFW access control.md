---
created: 2024-06-09T16:24:10+08:00
modified: 2024-06-09T16:28:43+08:00
---

# UFW access control

when using long range public wifi it matters to block every port from incoming connections.

```bash
sudo ufw default deny
sudo ufw prepend reject in on <intetfece name>
sudo ufw restart
```

when configuration is done, remember to restart ufw and reconnect existing interfaces.

although remote clients are blocked, self-issued connections are not.
