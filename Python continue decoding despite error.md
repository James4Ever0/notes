---
title: Python continue decoding despite error
created: '2024-07-01T09:37:13.022Z'
modified: '2024-07-01T09:42:11.292Z'
---

# Python continue decoding despite error

When using `chardet` you may get some confidence mark over a particular file. If that number is below one then you may face issues when decoding.

Specify `error=<error_handle_strategy>` can mitigate this issue.



