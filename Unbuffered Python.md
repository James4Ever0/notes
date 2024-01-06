---
title: Unbuffered Python
created: '2024-01-06T14:33:52.573Z'
modified: '2024-01-06T14:34:58.412Z'
---

# Unbuffered Python

When reading bytes asynchronously using `asyncio.create_subprocess_exec`, the program has to be unbuffered.

```bash
python3 -u <script_path>


```
