---
title: keep docker container running
created: '2024-07-04T09:59:48.415Z'
modified: '2024-07-04T10:01:11.518Z'
---

# keep docker container running

```bash
docker run -d <image_name> tail -f /dev/null
docker run -d <image_name> sleep infinity
docker run -dt <image_name>
docker run -dt <image_name> cat
docker run -d <image_name> nc -l -p <port>
```
