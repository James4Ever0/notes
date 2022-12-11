---
title: docker usage issues
created: '2022-12-11T00:21:44.329Z'
modified: '2022-12-11T00:24:21.234Z'
---

# docker usage issues

when exporting ports, if not specifying host ip, you cannot reach the service inside the container.

if you want to change ip routings or some other configurations passed when `docker run`, you need to change the file called `hostconfig.json` located in `/var/lib/docker/containers/<container_id>`
