---
title: Waydroid installation steps
created: '2023-12-21T15:43:49.506Z'
modified: '2023-12-21T15:50:24.219Z'
---

# Waydroid installation steps

cursed by the wall.

## install waydroid package (for ubuntu)

visit `` (``) `` (``) and download them as files.

comment out the download part in ``, move the certificate `` to ``, execute `` to setup waydroid repository

on ubuntu you need to use proxy during apt mirror syncing.

to setup proxy:

```bash

```

to use proxy:

```bash

```

after installation you should comment out the mirror at: ``

## initialize waydroid

the download speed of sourceforge is very slow, unless you use mirror like `liquidtelecom`

modify the file ``

```python

```

restart service: ``
