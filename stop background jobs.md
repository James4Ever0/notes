---
title: stop background jobs
created: '2023-01-10T03:00:06.770Z'
modified: '2023-01-10T03:00:27.518Z'
---

# stop background jobs

```bash
jobs | grep -Eo "[0-9][0-9][0-9]+" | xargs -iabc kill -s KILL abc
```

