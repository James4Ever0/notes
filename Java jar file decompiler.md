---
created: 2024-05-20T08:25:32+08:00
modified: 2024-05-20T08:56:02+08:00
---

# Java jar file decompiler

To decompile a single jar file we need more than just jd-core, which is a commandline tool to decompile a single class file at a time.

Use [jd-cli](https://github.com/intoolswetrust/jd-cli) which is downloadable at [here](https://github.com/intoolswetrust/jd-cli/releases/download/jd-cli-1.2.0/jd-cli-1.2.0-dist.tar.gz).

Commandline usage:

```bash
# without docker
java -jar jd-cli.jar file-to-decompile.jar -ods decompiled-src

# with docker
docker run -it --rm -v `pwd`:/mnt --user $(id -u):$(id -g) \
  kwart/jd-cli /mnt/file-to-decompile.jar -ods /mnt/decompiled-src
```

Full syntax:

```bash
Usage: java -jar jd-cli.jar [options] [Files to decompile]
  Options:
    --displayLineNumbers, -n
       displays line numbers in decompiled classes
       Default: false
    --escapeUnicodeCharacters, -eu
       escape unicode characters in decompiled classes
       Default: false
    --help, -h
       shows this help
       Default: false
    --logLevel, -g
       takes [level] as parameter and sets it as the CLI log level. Possible
       values are: ALL, TRACE, DEBUG, INFO, WARN, ERROR, OFF
       Default: INFO
    --outputConsole, -oc
       enables output to system output stream
       Default: false
    --outputDir, -od
       takes a [directoryPath] as a parameter and configures a flat DIR output
       for this path
    --outputDirStructured, -ods
       takes a [directoryPath] as a parameter and configures a structured DIR
       output for this path
    --outputZipFile, -oz
       takes a [zipFilePath] as a parameter and configures ZIP output for this
       path
    --pattern, -p
       RegExp pattern which the to-be-decompiled file has to match. Not matching
       entries are skipped.
    --serialProcessing, -sp
       don't use parallel processing
       Default: false
    --skipResources, -sr
       skips processing resources
       Default: false
    --version, -v
       shows the version
       Default: false
```
