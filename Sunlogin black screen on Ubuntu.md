---
title: Sunlogin black screen on Ubuntu
created: '2024-09-15T04:57:24.412Z'
modified: '2024-09-15T05:03:52.830Z'
---

# Sunlogin black screen on Ubuntu

First make sure only one user is using Sunlogin.

Next, switch to `lightdm` instead of `gdm3`:

```bash
sudo apt install -y lightdm
sudo dpkg-reconfigure lightdm
```

Finally, switch to Xorg instead of Wayland:


