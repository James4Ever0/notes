---
created: 2023-07-30T22:11:02+08:00
modified: 2023-07-30T22:14:29+08:00
---

# Docker container storage quota

`--storage-opt` is supported only for overlay over xfs with 'pquota' mount option.

change data-root to somewhere else in `/etc/docker/daemon.json`

edit `/etc/fstab` and add our xfs block on new line (find uuid using blkid)

```bash
docker run --storage-opt size=10M --rm -it alpine
```

when using [devmapper](https://docs.docker.com/storage/storagedriver/device-mapper-driver) make sure size is greater than 10G (default)

```bash
docker run --storage-opt size=11G --r'm -it alpine
```

zfs, vfs (not a unionfs, but for testing) storage drivers also supports disk quota. you may use it by changing `data-root` to the related storage device.
