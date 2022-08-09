---
title: find an unused random port and announce it on redis
created: '2022-08-09T06:15:35.018Z'
modified: '2022-08-09T06:18:37.436Z'
---

# find an unused random port and announce it on redis

issues were found when launching apps on fixed ports.

python to get unused port:
```python
def getUnusedLocalhostPort():
    """
    These were "Borrowed" from YCM.
    See https://github.com/Valloric/YouCompleteMe
    """
    sock = socket.socket()
    # This tells the OS to give us any free port in the range [1024 - 65535]
    sock.bind(("", 0))
    port = sock.getsockname()[1]
    sock.close()
    return port
```

python send port to redis:
```python

```
