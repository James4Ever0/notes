---
title: docker usage issues
created: '2022-12-11T00:21:44.329Z'
modified: '2022-12-11T13:21:44.618Z'
---

# docker usage issues

when exporting ports, if not specifying host ip, you cannot reach the service inside the container. do this instead: `docker run -p 0.0.0.0:<host_port>:<container_port> <rest_commands>`

it seems to be the proxy. disable http proxy so we can connect to container again.

if you want to change ip routings or some other configurations passed when `docker run`, you need to change the file called `hostconfig.json` located in `/var/lib/docker/containers/<container_id>` with `PortBindings` sections. you stop the container first. find and change the config file then start it. [tutorial](https://ahelpme.com/software/docker/docker-change-the-port-mapping-of-an-existing-container/#:~:text=Here%20is%20the%20whole%20procedure%3A%201%20Stop%20the,Docker%20container%20service.%205%20Start%20the%20docker%20container.)

containers can only contact each other if they share the same network. better give unique ip for each container within same network. it can also use container name as host name instead of static ip. [tutorial](https://maximorlov.com/4-reasons-why-your-docker-containers-cant-talk-to-each-other/)

create a network (not overlapping with anything shown in `ifconfig`, notice the subnet mask):

```bash
docker network create --subnet=172.18.0.0/16 <network_name>
```

start container with given network (again not overlapping with addresses in `ifconfig`, not the starting address):

```bash
docker run --rm -d -it --net <network_name> --ip <ipaddress> --name <container_name>
```
to check what ip the container is at:

```bash
docker inspect <container_id/container_name> | grep IPAddress
```

now you might can talk to the container.
