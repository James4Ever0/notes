---
title: 'System lagging alert, temperature alert in arbitrary device'
created: '2024-01-14T05:48:29.112Z'
modified: '2024-01-14T09:45:24.505Z'
---

# System lagging alert, temperature alert in arbitrary device

The system sometimes feels lagging, less responsive. The only way to fix is to reboot.

Although monitor task completion time is helpful, but not general enough.

Simple hack:

```python

```

Lagging related package:

```bash
apt install nohang oomd psi-notify 
```

---

Temperature monitoring packages:

```bash
pip3 install gpustat
pip3 install pyspectator
apt install lm-sensor # sensors -j
```

Create temperature statistics (high, low, mean) for all crucial components.

Set alert threshold, only trigger alert if temperature reoccurs for several times.

Send `ntfy.io` notification as well as making audible alerts.

Notification shall specify device name, component name, current temperature, threshold, statistics.

Every device shall be equipped with this software as daemon, be it smartphone, MacBook, Linux PC, Windows PC.
