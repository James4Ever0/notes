---
title: 'System lagging alert, Temperature alert in arbitrary device'
created: '2024-01-14T05:48:29.112Z'
modified: '2024-01-14T08:58:04.850Z'
---

# System lagging alert, Temperature alert in arbitrary device

The system sometimes feels lagging, less responsive. The only way to fix is to reboot.

Although monitor task completion time is helpful, but not general enough.

Temperature monitoring packages:

```bash
pip3 install gpustat
pip3 install pyspectator
apt install lm-sensor # sensor -j
```

Create temperature statistics (high, low, mean) for all crucial components.

Set alert threshold, only trigger alert if temperature reoccurs for several times.

Send `ntfy.io` notification as well as making audible alerts.

Notification shall specify device name, component name, current temperature, threshold, statistics.

Every device shall be equipped with this software as daemon, be it smartphone, MacBook, Linux PC, Windows PC.
