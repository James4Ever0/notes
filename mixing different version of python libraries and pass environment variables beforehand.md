---
title: mixing different version of python libraries and pass environment variables beforehand
created: '2022-11-04T13:45:04.450Z'
modified: '2022-11-04T13:48:20.338Z'
---

# mixing different version of python libraries and pass environment variables beforehand

command of `mpython3`

```bash
env JAVA_HOME=/opt/homebrew/Cellar/openjdk/18.0.2 PYTHONPATH=$(python3 -c "import sys; print(':'.join(sys.path))"):/opt/homebrew/lib/python3.10/site-packages python3 $@
```
