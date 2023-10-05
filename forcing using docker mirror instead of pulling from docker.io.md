---
title: forcing using docker mirror instead of pulling from docker.io
created: '2023-10-05T15:34:18.836Z'
modified: '2023-10-05T15:35:47.862Z'
---

# forcing using docker mirror instead of pulling from docker.io

even if you configure `/etc/docker/daemon.json` like this:

```json

```

it is not working now until:
```bash
sudo -E docker pull mirror.baidubce.com/significantgravitas/auto-gpt
```

---

docker mirrors:

```

```
