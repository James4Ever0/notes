---
title: Sunlogin black screen on Ubuntu
created: '2024-09-15T04:57:24.412Z'
modified: '2024-09-15T04:59:57.883Z'
---

# Sunlogin black screen on Ubuntu

You need first switch to Xorg instead of Wayland.

Next make sure only one user is using Sunlogin.

Finally, switch to `lightdm` instead of `gdm3`:

```bash
sudo apt install -y lightdm
sudo dpkg-reconfigure lightdm
```
