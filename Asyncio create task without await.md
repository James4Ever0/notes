---
created: 2026-04-02T18:42:02+08:00
modified: 2026-04-02T18:42:18+08:00
---

# Asyncio create task without await

If you create an asyncio task with `asyncio.create_task()` and then sleep (e.g., `await asyncio.sleep(3)`) **without** awaiting the task itself, the task will still run concurrently during that sleep. The event loop will switch to the task, execute its code (including the `print` statement), and then resume the sleep.

So in your scenario—where the task only contains a `print`—you **will see the printed output** even without awaiting the task. The side effect (printing) happens as soon as the task runs.

However, if you meant “get the result” as the **return value** of the coroutine (e.g., if it returned a string or number), you cannot obtain that without either:
- `await task` (which would also wait for completion), or
- calling `task.result()` after the task is done (which requires checking `task.done()` or using a callback).

**Important notes:**
- The event loop must keep running long enough for the task to finish. In your example, `asyncio.sleep(3)` gives it that time.
- If you don’t keep a reference to the task and the program ends immediately after the sleep, the task may be cancelled or garbage‑collected before completing. But as long as you await the sleep (or otherwise keep the loop alive), the task runs fine.

**Example that prints the output without awaiting the task:**
```python
import asyncio

async def my_task():
    print("Hello from task")
    # No return value, just print

async def main():
    task = asyncio.create_task(my_task())
    await asyncio.sleep(3)   # task runs during this sleep
    # task not awaited – but print already happened

asyncio.run(main())
```
Output: `Hello from task`

If the task returned a value (e.g., `return 42`), you would **not** get `42` without awaiting `task` or calling `task.result()` after it finishes.
