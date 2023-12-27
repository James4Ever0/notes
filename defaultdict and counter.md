---
title: defaultdict and counter
created: '2023-12-27T17:08:40.623Z'
modified: '2023-12-27T17:13:59.614Z'
---

# defaultdict and counter

```python
from collections import defaultdict, Counter
mydict = defaultdict(Counter) # remember to put callable or none as argument of defaultdict
mydict = defaultdict(lambda: defaultdict(lambda: 0)) #alternative
mydict['k1']['k2'] += 1 # it is ok
```
