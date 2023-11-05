---
title: Home Assistant Installation & Setups
created: '2023-11-05T18:51:22.434Z'
modified: '2023-11-05T19:13:06.544Z'
---

# Home Assistant Installation & Setups

Fully functional HA mainly comes into two forms: flashable supervised `.iso` images, and virtual machines (not docker container).

Remember to create backup of HA after successful initialization. You can create an iso for the entire disk or just using backup utility builtin.

Supervisor need to be updated before other components. It is also the troublemaker. Set auto update of supervisor to false by:

```bash
ha supervisor options --auto-update=false
```

Since its heavy reliance on docker and github, one need to use [OpenClash](https://github.com/vernesong/OpenClash) along with [OpenWrt](https://openwrt.org/) flashed in one dedicated router like [NanoPi R2S](https://openwrt.org/toh/friendlyarm/nanopi_r2s) to smooth the installation process.

Use video capture card and OBS studio to observe the RPI terminal. Attach to keyboard to type commands.

`ha banner` sometimes resolves issues.

To prevent addon installation limits, you can enter [debug mode](https://developers.home-assistant.io/docs/operating-system/debugging/), edit the following file `/mnt/data/supervisor/jobs.json` into:

```json
{
  "ignore_conditions": [
    "healthy"
  ]
}
```

Some files like `/etc/docker/daemon.json`, `/etc/hosts` cannot be changed after boot. You can change them before boot using card reader.
