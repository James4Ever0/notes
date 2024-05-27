---
title: IP info collect
created: '2024-05-27T03:18:04.490Z'
modified: '2024-05-27T03:41:42.033Z'
---

# IP info collect

Tutorial:

https://stackoverflow.com/questions/24678308/how-to-find-location-with-ip-address-in-python

To obtain IP of ourselves, we can visit:



To get geo info of our IP, visit:

```bash
curl https://ipinfo.io | jq .country
```

TO get geo info of any IP, use:

https://pypi.org/project/IP2Location/

https://ip2location-python.readthedocs.io/en/latest/quickstart.html
