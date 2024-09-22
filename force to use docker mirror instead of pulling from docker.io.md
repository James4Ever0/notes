---
title: force to use docker mirror instead of pulling from docker.io
created: '2023-10-05T15:34:18.836Z'
modified: '2024-09-22T05:32:53.989Z'
---

# force to use docker mirror instead of pulling from docker.io

https://jockerhub.com/

---

even if you configure `/etc/docker/daemon.json` like this (note: you still need to do this):

```json
{ "registry-mirrors": 
	["https://mirror.baidubce.com"]
}
```

it is not fully working until:

```bash
sudo -E docker pull mirror.baidubce.com/significantgravitas/auto-gpt
```
