---
title: do not use better_exception with multithreading or multiprocessing
created: '2024-03-13T01:27:41.359Z'
modified: '2024-03-13T01:28:59.862Z'
---

# do not use better_exception with multithreading or multiprocessing

when using it with things like `sse_starlette`, traceback of child process/thread will be invisible.
