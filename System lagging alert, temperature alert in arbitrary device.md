---
title: 'System lagging alert, temperature alert in arbitrary device'
created: '2024-01-14T05:48:29.112Z'
modified: '2024-01-14T11:18:20.727Z'
---

# System lagging alert, temperature alert in arbitrary device

The system sometimes feels lagging, less responsive. The only way to fix is to reboot.

Although monitor task completion time is helpful, but not general enough.

Simple hack:

```python
import subprocess

def measure_system_responsiveness():
    start_time = time.time()
    subprocess.run(
        ["echo", "hello"], capture_output=True, encoding='utf-8', check=True
    )
    end_time = time.time()
    exec_time = end_time - start_time
    exec_per_second = 1 / exec_time
    return exec_per_second
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

Send `ntfy.sh` notification as well as making audible alerts.

Notification shall specify device name, component name, current temperature, threshold, statistics.

Every device shall be equipped with this software as daemon, be it smartphone, MacBook, Linux PC, Windows PC.
