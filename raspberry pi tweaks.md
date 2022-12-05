---
title: raspberry pi tweaks
created: '2022-12-05T11:54:42.089Z'
modified: '2022-12-05T19:54:06.679Z'
---

# raspberry pi tweaks

you've installed [raspap](https://raspap.com/) on this device. you use the default credentials. this shit will not connect to our wifi automatically, thus block your way of running docker containers on it with only macbook.

seriously? do you really need docker on macos? or just on raspberry pi?

```bash
sudo apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1080/"  -o Acquire::Check-Valid-Until=false -o Acquire::Check-Date=false  update --allow-releaseinfo-change
```
