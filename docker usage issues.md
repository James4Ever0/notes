---
title: docker usage issues
created: '2022-12-11T00:21:44.329Z'
modified: '2022-12-11T00:25:24.857Z'
---

# docker usage issues

when exporting ports, if not specifying host ip, you cannot reach the service inside the container. do this instead: `docker run -p 0.0.0.0:

if you want to change ip routings or some other configurations passed when `docker run`, you need to change the file called `hostconfig.json` located in `/var/lib/docker/containers/<container_id>` with `PortBindings` sections.
