---
title: defaultdict and counter
created: '2023-12-27T17:08:40.623Z'
modified: '2023-12-27T17:09:36.533Z'
---

# defaultdict and counter

```python
from collections import defaultdict, Counter
mydict = defaultdict(Counter)
mydict['k1']['k2'] += 1 # it is ok
```
