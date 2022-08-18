---
tags: [package manager, self-signed certificate, system manage]
title: issues related to fastgithub and other self-signed certificates in language-specific package managers
created: '2022-08-15T07:44:43.828Z'
modified: '2022-08-18T07:40:04.301Z'
---

# issues related to fastgithub and other self-signed certificates in language-specific package managers

## npm

[npm报错：unable to verify the first certificate](https://blog.csdn.net/fclwd/article/details/79894251)

```bash
npm config set strict-ssl false
npm config set ca=""
```

npm download binary files from github will raise error since the download speed is low.

use `cnpm` instead, since it will route all github binary requests to mirrored cnpm cdn.
```bash
npm i -g cnpm
```

set some binary distribution file mirror to `https://registry.npmmirror.com` in `~/.npmrc` and `~/.yarnrc`:
```config
canvas_binary_host_mirror=https://registry.npmmirror.com/-/binary/canvas/
sass_binary_site=https://registry.npmmirror.com/-/binary/node-sass
nodejs_org_mirror=https://registry.npmmirror.com/-/binary/node/
electron_mirror=https://registry.npmmirror.com/-/binary/electron/
electron_builder_binaries_mirror=https://registry.npmmirror.com/-/binary/electron-builder-binaries/
chromedriver_cdnurl=https://registry.npmmirror.com/-/binary/chromedriver/

registry=https://registry.npmmirror.com

```
