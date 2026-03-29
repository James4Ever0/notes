---
created: 2026-03-29T23:59:32+08:00
modified: 2026-03-29T23:59:48+08:00
---

# Run blocking task with asyncio

Below is a complete example showing how to run a blocking function in a **separate executor** using `asyncio.run_in_executor()`. It also addresses your second question about passing an async function (coroutine) to `run_in_executor` without `await`.

## Full Example: Running Blocking Functions in a Custom Executor

```python
import asyncio
import time
from concurrent.futures import ThreadPoolExecutor

# A blocking function (e.g., I/O or CPU-bound work)
def blocking_task(name: str, duration: float) -> str:
    print(f"  [{name}] starting blocking work for {duration}s...")
    time.sleep(duration)          # Simulates blocking operation (e.g., file I/O, heavy computation)
    print(f"  [{name}] finished")
    return f"Result from {name}"

async def main():
    # Create a separate executor (e.g., with max 3 worker threads)
    # You can also use ProcessPoolExecutor for CPU-bound tasks.
    with ThreadPoolExecutor(max_workers=3) as executor:
        # Get the current event loop
        loop = asyncio.get_running_loop()

        # Schedule blocking functions to run in the executor.
        # run_in_executor returns an awaitable that yields the result.
        task1 = loop.run_in_executor(executor, blocking_task, "A", 2)
        task2 = loop.run_in_executor(executor, blocking_task, "B", 1)
        task3 = loop.run_in_executor(executor, blocking_task, "C", 3)

        # Wait for all results concurrently (non‑blocking for asyncio)
        results = await asyncio.gather(task1, task2, task3)

        print("\nAll results:", results)

if __name__ == "__main__":
    asyncio.run(main())
```

**Output** (order may vary due to different durations):
```
  [B] starting blocking work for 1s...
  [A] starting blocking work for 2s...
  [C] starting blocking work for 3s...
  [B] finished
  [A] finished
  [C] finished

All results: ['Result from A', 'Result from B', 'Result from C']
```

### Alternative: `asyncio.to_thread()` (Python 3.9+)
For simpler use cases, `asyncio.to_thread()` uses the default executor but is more concise:
```python
result = await asyncio.to_thread(blocking_task, "A", 2)
```
To use a **custom executor** with `to_thread`, you would first set it as the default:
```python
loop = asyncio.get_running_loop()
loop.set_default_executor(ThreadPoolExecutor(max_workers=3))
```

---

## Can I Pass an Async Function Call Without `await` into `run_in_executor`?

**Short answer: No – it won't work as you expect.**

`run_in_executor` expects a **regular callable** (function, lambda, etc.) that returns a value directly. If you pass an **async function** (a coroutine) without calling it, you get a coroutine object – but `run_in_executor` will never `await` it, so it won't execute. If you call the async function (e.g., `my_async_func()`), that returns a coroutine object, which is still not a regular value.

### What happens if you try?
```python
async def async_greeting():
    await asyncio.sleep(0.1)
    return "Hello"

# Wrong usage:
future = loop.run_in_executor(executor, async_greeting)   # ❌ passes coroutine function
result = await future  # The function itself runs in the thread, not the coroutine!
# Output: <coroutine object async_greeting at ...> – not "Hello"

# Also wrong:
future = loop.run_in_executor(executor, async_greeting()) # ❌ passes a coroutine object
# run_in_executor will try to call the coroutine object, which raises TypeError.
```

### How to properly run an async function in an executor?
If you really need to run an **asynchronous** function inside a separate thread (rarely necessary – usually you just `await` it directly), you must create a new event loop inside that thread. Example:

```python
def run_async_in_thread(async_func, *args):
    """Run an async function in a separate thread."""
    new_loop = asyncio.new_event_loop()
    asyncio.set_event_loop(new_loop)
    try:
        return new_loop.run_until_complete(async_func(*args))
    finally:
        new_loop.close()

# Usage:
async def my_async_task(x):
    await asyncio.sleep(0.5)
    return x * 2

# Schedule it in the executor
future = loop.run_in_executor(executor, run_async_in_thread, my_async_task, 5)
result = await future
print(result)  # 10
```

But this is **almost never needed**. If you already have an asyncio event loop, just `await my_async_task(5)` directly – that's the whole point of async/await.

### Summary
- **Blocking functions** → `run_in_executor` or `asyncio.to_thread()`
- **Async functions** → `await` them directly (or use `asyncio.create_task` for concurrency)
- Do **not** pass async functions to `run_in_executor`; it will not run their coroutine logic correctly.
