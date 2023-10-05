---
title: forcing using docker mirror instead of pulling from docker.io
created: '2023-10-05T15:34:18.836Z'
modified: '2023-10-05T15:37:10.574Z'
---

# forcing using docker mirror instead of pulling from docker.io

even if you configure `/etc/docker/daemon.json` like this:

```json
{ "registry-mirrors": 
	["https://mirror.baidubce.com"]
}
```

it is not working until:

```bash
sudo -E docker pull mirror.baidubce.com/significantgravitas/auto-gpt
```
