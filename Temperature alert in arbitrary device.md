---
title: Temperature alert in arbitrary device
created: '2024-01-14T05:48:29.112Z'
modified: '2024-01-14T08:25:02.953Z'
---

# Temperature alert in arbitrary device

Temperature monitoring packages:

```
gpustat
pyspectator
```

Create temperature statistics (high, low, mean) for all crucial components.

Set alert threshold, only trigger alert if temperature reoccurs for several times.

Send `ntfy.io` notification as well as making audible alerts.

Notification shall specify device name, component name, current temperature, threshold, statistics.

Every device shall be equipped with this software as daemon, be it smartphone, MacBook, Linux PC, Windows PC.
