---
title: issues related to fastgithub and other self-signed certificates in package manager
created: '2022-08-15T07:44:43.828Z'
modified: '2022-08-15T08:19:58.640Z'
---

# issues related to fastgithub and other self-signed certificates in package manager

## npm

[npm报错：unable to verify the first certificate](https://blog.csdn.net/fclwd/article/details/79894251)

```bash
npm config set strict-ssl false
npm config set ca=""
```

npm download binary files from github will raise error since the download speed is low.

set some binary distribution file mirror to `https://registry.npmmirror.com`:
```bash

```
