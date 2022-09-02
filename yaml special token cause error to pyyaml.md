---
title: yaml special token cause error to pyyaml
created: '2022-09-02T06:25:33.284Z'
modified: '2022-09-02T06:29:13.246Z'
---

# yaml special token cause error to pyyaml

special token like `!<str>` need to be converted to `!!str`, while writing back we just do it in reverse.

full reference of pyyaml is [here](https://pyyaml.org/wiki/PyYAMLDocumentation)
