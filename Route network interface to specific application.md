---
title: Route network interface to specific application
created: '2024-06-03T06:30:04.514Z'
modified: '2024-06-03T06:33:53.527Z'
---

# Route network interface to specific application

It is not advised to do so with dual wifi connection. Have not tested with ethernet and wifi dual connection.

---

use firejail

```bash
sudo firejail --net=wlan0 --ip=dhcp --noprofile <program cmd>
```

---

use dante and proxychains-ng

```bash
sudo apt install dante-server
```

now edit the dante config file:

```

```

run the program with proxychains-ng:

```bash

```
