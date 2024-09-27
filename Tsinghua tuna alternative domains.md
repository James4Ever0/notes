---
title: Tsinghua tuna alternative domains
created: '2024-09-27T16:17:19.778Z'
modified: '2024-09-27T16:20:10.787Z'
---

# Tsinghua tuna alternative domains

You can use the below domains:

```
https://mirrors.tuna.tsinghua.edu.cn
https://mirrors6.tuna.tsinghua.edu.cn
```

If you have encountered anything like connection error while using Tuna mirrors, please save the below script as `noproxy` and run the previous command with it.

```bash
#!/bin/bash
env http_proxy="" https_proxy="" noproxy="" $@
```
