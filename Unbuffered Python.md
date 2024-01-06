---
title: Unbuffered Python
created: '2024-01-06T14:33:52.573Z'
modified: '2024-01-06T14:35:17.862Z'
---

# Unbuffered Python

When reading bytes asynchronously using `asyncio.create_subprocess_exec`, the program has to be unbuffered.

```bash
python3 -u <script_path>
```

```python
# this can only make `print` into unbuffered

```
