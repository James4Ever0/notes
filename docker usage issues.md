---
title: docker usage issues
created: '2022-12-11T00:21:44.329Z'
modified: '2024-06-26T06:31:47.083Z'
---

# docker usage issues

latest docker mirror:

https://zhuanlan.zhihu.com/p/704011584

---

login mysql with empty password then execute command to make it remotely available:
```bash
mysql -uroot --password= -e "grant all privileges on *.* to root@'%' identified by '' with grant option; commit;"
```

create volume and attach volume to container, since containers will be reset after system restarts.

```bash
docker volume create <volume_name>
docker run -it -d --rm -v <volume_name>:<container_mountpoint> --name <container_name> <image_name>
docker volume inspect <volume_name> # get info on created volume
```

when using mindsdb, it sucks because having bad pypi mirrors.

set pip index url globally:
```bash
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

or pass it as environment variable:

```bash
docker run -it -d -e PIP_INDEX_URL=https://pypi.tuna.tsinghua.edu.cn/simple -n <container_name> <image_name>
```

if you want to save container states into images, use `docker commit <container_name> <image_name>[:image_tag]`

Keep in mind that the `docker commit` command only saves the changes made to a container's file system. It does not save any changes made to the container's settings or network configurations. To save all changes made to a container, including settings and network configurations, you can use the `docker export` and `docker import` commands instead.

when exporting ports, if not specifying host ip, you cannot reach the service inside the container. do this instead: `docker run -p 0.0.0.0:<host_port>:<container_port> <rest_commands>`

it seems to be the proxy (fastgithub). disable http proxy so we can connect to container again, or use clash to make rules to let "localhost" or subnet requests passing through.

if you want to change ip routings or some other configurations passed when `docker run`, you need to change the file called `hostconfig.json` located in `/var/lib/docker/containers/<container_id>` with `PortBindings` sections. you stop the container first. find and change the config file then start it. [tutorial](https://ahelpme.com/software/docker/docker-change-the-port-mapping-of-an-existing-container/#:~:text=Here%20is%20the%20whole%20procedure%3A%201%20Stop%20the,Docker%20container%20service.%205%20Start%20the%20docker%20container.)

seems not working. fuck.

```

"PortBindings": {
    "80/tcp": [
        {
            "HostPort": "8080"
        }
    ],
}
```

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

now you might can talk to the container without port mappings.
