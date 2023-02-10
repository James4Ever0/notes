---
title: using default pypi.org/simple index
created: '2023-02-10T12:51:19.069Z'
modified: '2023-02-10T12:54:56.072Z'
---

# using default pypi.org/simple index

packages like `EdgeGPT` may update overnight. mirrors won't keep up. you need to fetch from the official package index.

----

to set the index:

```bash
pip set global.index-url https://pypi.org/simple
```

to use the index temporarily:

```bash
pip install <package> -i https://pypi.org/simple
```
