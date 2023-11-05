---
title: Home Assistant Installation & Setups
created: '2023-11-05T18:51:22.434Z'
modified: '2023-11-05T19:01:25.902Z'
---

# Home Assistant Installation & Setups

Fully functional HA mainly comes into two forms: flashable supervised `.iso` images, and virtual machines (not docker container).

Supervisor need to be updated before other components.

```bash
ha supervisor options --auto-update=false
```

Since its heavy reliance on docker and github, one need to use [OpenClash]() along with [OpenWrt]() flashed in one dedicated router like [NanoPi R2S]() to smooth the installation process.

Use video capture card and OBS studio to observe the RPI terminal. Attach to keyboard to type commands.

You can enter [debug mode](https://developers.home-assistant.io/docs/operating-system/debugging/), change the following files:

Some files like `/etc/docker/daemon.json`, `/etc/hosts` cannot be changed after boot. You can change them before boot using card reader.
