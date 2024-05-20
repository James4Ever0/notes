---
created: 2024-05-20T08:25:32+08:00
modified: 2024-05-20T08:32:00+08:00
---

# Java jar file decompiler

To decompile a single jar file we need more than just jd-core, which is a commandline tool to decompile a single class file at a time.

Use [jd-cli](https://github.com/intoolswetrust/jd-cli) which is downloadable at [here](https://github.com/intoolswetrust/jd-cli/releases).

Commandline usage:

```bash
# without docker
java -jar jd-cli.jar file-to-decompile.jar -ods decompiled-src

# with docker
docker run -it --rm -v `pwd`:/mnt --user $(id -u):$(id -g) \
  kwart/jd-cli /mnt/file-to-decompile.jar -ods /mnt/decompiled-src```
