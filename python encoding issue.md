---
title: python encoding issue
created: '2023-07-05T09:39:32.530Z'
modified: '2023-07-05T09:43:17.998Z'
---

# python encoding issue

windows has encoding issue on python intepreter.

run like this:
```bash
python -X utf8=1 <args>
# flag: sys.flags.utf8_mode
```

