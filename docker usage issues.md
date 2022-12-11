---
title: docker usage issues
created: '2022-12-11T00:21:44.329Z'
modified: '2022-12-11T00:39:44.930Z'
---

# docker usage issues

when exporting ports, if not specifying host ip, you cannot reach the service inside the container. do this instead: `docker run -p 0.0.0.0:<host_port>:<container_port> <rest_commands>`

it seems to be the proxy. disable http proxy so we can connect to container again.

if you want to change ip routings or some other configurations passed when `docker run`, you need to change the file called `hostconfig.json` located in `/var/lib/docker/containers/<container_id>` with `PortBindings` sections. you stop the container first. find and change the config file then start it. [tutorial](https://ahelpme.com/software/docker/docker-change-the-port-mapping-of-an-existing-container/#:~:text=Here%20is%20the%20whole%20procedure%3A%201%20Stop%20the,Docker%20container%20service.%205%20Start%20the%20docker%20container.)

containers can only contact each other if they share the same network. better give unique ip for each container within same network. it can also use container name as host name instead of static ip. [tutorial](https://maximorlov.com/4-reasons-why-your-docker-containers-cant-talk-to-each-other/)
