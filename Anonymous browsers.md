---
title: Anonymous browsers
created: '2024-05-27T02:55:33.180Z'
modified: '2024-05-27T06:53:29.858Z'
---

# Anonymous browsers

There are three kinds of anonymous browsers.

- Container based, remote desktop connected browsers

```bash
docker pull linuxserver/firefox

# valina base image, without Unicode support
docker run -d --name firefox_browser --rm --expose 3000:3000 linuxserver/firefox

# configure `/System/Library/Fonts` to be available in Docker.app first then run this command
docker run -v /System/Library/Fonts:/usr/share/fonts:ro --name firefox_browser -d --rm -p 3000:3000 linuxserver/firefox

# Ubuntu and other Linux
docker run -v /usr/share/fonts:/usr/share/fonts:ro --name firefox_browser -d --rm -p 3000:3000 linuxserver/firefox

# Official Unicode support
docker run -e DOCKER_MODS=linuxserver/mods:universal-package-install -e INSTALL_PACKAGES=font-noto-cjk -e LC_ALL=zh_CN.UTF-8 --name firefox_browser -d --rm -p 3000:3000 linuxserver/firefox
```

- Container based, browser-in-browser emulation based

https://github.com/titaniumnetwork-dev/Ultraviolet-App/wiki/Deploy-via-terminal

https://github.com/BrowserBox/BrowserBox

- Builtin anonymous browser like Tor browser

