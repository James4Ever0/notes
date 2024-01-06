---
title: Unbuffered Python
created: '2024-01-06T14:33:52.573Z'
modified: '2024-01-06T14:36:04.172Z'
---

# Unbuffered Python

When reading bytes asynchronously using `asyncio.create_subprocess_exec`, the program has to be unbuffered.

```bash
python3 -u <script_path>
```

```python
# this can only make `print` into unbuffered
import builtins
import copy

old_print = copy.copy(builtins.print)

def custom_print(*args, **kwargs):
    if 'flush' not in kwargs:
        kwargs['flush'] = True
    old_print(*args, **kwargs)

# Override the built-in print function with the custom function
builtins.print = custom_print
```
