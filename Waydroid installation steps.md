---
title: Waydroid installation steps
created: '2023-12-21T15:43:49.506Z'
modified: '2023-12-21T15:58:06.214Z'
---

# Waydroid installation steps

cursed by the wall.

## install waydroid package (for ubuntu)

visit `` (``) `` (``) and download them as files. (using proxy)

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

start waydroid service: 

the download speed of sourceforge is very slow, unless you use mirror like `liquidtelecom`

modify the file ``

```python

```

restart service: `sudo systemctl restart waydroid-container`

run command `sudo waydroid init`

## run waydroid in xorg

install weston: `apt install weston`

configure weston at `~/.config/weston.ini`

```toml

```

run `weston`, launch terminal at top left corner, run `waydroid`
