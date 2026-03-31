---
created: 2026-03-31T15:25:10+08:00
modified: 2026-03-31T15:25:53+08:00
---

# resolve there is no current event loop in thread xxx in python asyncio

# Resolving "There is No Current Event Loop in Thread" Error

The error `RuntimeError: There is no current event loop in thread 'threadpoolexecutor-0_0'` occurs when you try to use `asyncio.get_event_loop()` in a thread other than the main thread. This is because asyncio only generates an event loop for the main thread by default.

## Example

```python
import asyncio
from concurrent.futures import ThreadPoolExecutor

def run_async_code():
    loop = asyncio.get_event_loop()
    loop.run_until_complete(async_task())

async def async_task():
    print("Running async task")

executor = ThreadPoolExecutor(max_workers=1)
executor.submit(run_async_code)
```

**Error:**

```
RuntimeError: There is no current event loop in thread 'ThreadPoolExecutor-0_0'
```

## Solution 1: Create a New Event Loop

To resolve this, you can create a new event loop and set it for the current thread.

### Example:

```python
import asyncio
from concurrent.futures import ThreadPoolExecutor

def run_async_code():
    loop = asyncio.new_event_loop()
    asyncio.set_event_loop(loop)
    loop.run_until_complete(async_task())

async def async_task():
    print("Running async task")

executor = ThreadPoolExecutor(max_workers=1)
executor.submit(run_async_code)
```

## Solution 2: Use `asyncio.run()`

Another approach is to use `asyncio.run()` which creates a new event loop and closes it when finished.

### Example:

```python
import asyncio
from concurrent.futures import ThreadPoolExecutor

def run_async_code():
    asyncio.run(async_task())

async def async_task():
    print("Running async task")

executor = ThreadPoolExecutor(max_workers=1)
executor.submit(run_async_code)
```

By following these solutions, you can resolve the `RuntimeError` and ensure that your asynchronous code runs smoothly in threads other than the main thread.
