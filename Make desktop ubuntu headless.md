---
created: 2024-07-24T10:34:00+08:00
modified: 2024-07-24T10:34:52+08:00
---

# Make desktop ubuntu headless

```bash
sudo apt-get purge libx11* libqt*
sudo apt-get autoremove -y
sudo apt-get clean
```
