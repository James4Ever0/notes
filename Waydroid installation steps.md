---
title: Waydroid installation steps
created: '2023-12-21T15:43:49.506Z'
modified: '2023-12-21T16:05:43.652Z'
---

# Waydroid installation steps

cursed by the wall.

## install waydroid package (for ubuntu)

visit `` (``) `` (``) and download them as files. (using proxy)

comment out the download part in ``, move the certificate `` to ``, execute `` to setup waydroid repository

on ubuntu you need to use proxy during apt mirror syncing.

to setup proxy:

```bash
 proxy --port <port> --host <host> \
                                     --plugins proxy.plugin.ProxyPoolPlugin \
                                     --proxy-pool localhost:<local_proxy_port>
```

to use proxy:

```bash
sudo env https_proxy=http://<host>:<port> http_proxy=http://<host>:<port> all_proxy=http://<host>:<port> apt update

sudo env https_proxy=http://<host>:<port> http_proxy=http://<host>:<port> all_proxy=http://<host>:<port> apt install waydroid -y
```

after installation you should comment out the mirror at: `/etc/apt/sources.list.d/waydroid.list`

## initialize waydroid

start waydroid service: `sudo systemctl enable --now waydroid-container`

the download speed of sourceforge is very slow, unless you use mirror like `liquidtelecom`

modify the file `/usr/lib/waydroid/tools/helpers/http.py`

```python
...

## added part

def is_sourceforge_download_url(url: str):
    keywords = ["sourceforge.net", "download"]
    return all([kw in url for kw in keywords])

def use_liquidtelecom_mirror(url: str):
    # example: https://sourceforge.net/projects/waydroid/files/images/system/lineage/waydroid_x86_64/lineage-18.1-20231216-VANILLA-waydroid_x86_64-system.zip/download
    #      ->  https://sourceforge.net/projects/waydroid/files/images/system/lineage/waydroid_x86_64/lineage-18.1-20231216-VANILLA-waydroid_x86_64-system.zip/download?use_mirror=liquidtelecom
    keyword = "use_mirror=liquidtelecom"
    if is_sourceforge_download_url(url):
        if keyword not in url:
            conn_symbol = "?" if "?" not in url else "&"
            url += conn_symbol + keyword
    return url

## modify part

def download(args, url, prefix, cache=True, loglevel=logging.INFO, allow_404=False):
    ...
    url = use_liquidtelecom_mirror(url)
    ...

...
```

restart service: `sudo systemctl restart waydroid-container`

run command `sudo waydroid init`

## run waydroid in xorg

install weston: `apt install weston`

configure weston at `~/.config/weston.ini`

```toml

```

run `weston`, launch terminal at top left corner, run `waydroid`
