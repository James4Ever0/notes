---
title: Anonymous browsers
created: '2024-05-27T02:55:33.180Z'
modified: '2024-05-27T05:59:29.380Z'
---

# Anonymous browsers

There are three kinds of anonymous browsers.

- Container based, remote desktop connected browsers

```bash
docker pull linuxserver/firefox
docker run -d --name firefox_browser --rm --expose 3000:3000 linuxserver/firefox
```

- Container based, browser-in-browser emulation based

https://github.com/titaniumnetwork-dev/Ultraviolet-App/wiki/Deploy-via-terminal

https://github.com/BrowserBox/BrowserBox

- Builtin anonymous browser like Tor browser

