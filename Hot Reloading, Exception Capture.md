---
title: 'Hot Reloading, Exception Capture'
created: '2022-11-08T05:51:45.546Z'
modified: '2022-11-08T05:55:39.923Z'
---

# Hot Reloading, Exception Capture

DevPy can capture every exception at the time it is raised, no matter it is wrapped around some 'try-except' or not.

[Reloadium](https://github.com/reloadware/reloadium) requires breakpoints to reload scripts. However, breakpoints can be generated/inferenced and removed at runtime. Currently it only works with [pydevd](https://github.com/fabioz/PyDev.Debugger) inside pycharm. Reloadium supports line-wise profiling.
