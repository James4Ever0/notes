---
title: 'Hot Reloading, Exception Capture'
created: '2022-11-08T05:51:45.546Z'
modified: '2022-11-08T06:02:28.192Z'
---

# Hot Reloading, Exception Capture

[DebugPy](https://github.com/microsoft/debugpy) can capture every exception [at the time it is raised](https://github.com/microsoft/debugpy/blob/8157273a28b5d4d1ea49fe90eb51f9f1c19b80dc/src/debugpy/_vendored/pydevd/_pydevd_bundle/pydevd_frame.py), no matter it is wrapped around some 'try-except' or not.

[Reloadium](https://github.com/reloadware/reloadium) requires breakpoints to reload scripts. However, breakpoints can be generated/inferenced and removed at runtime. Currently it only works with [pydevd](https://github.com/fabioz/PyDev.Debugger) inside pycharm. Reloadium supports line-wise profiling.

[Debug Adapter Protocol](https://microsoft.github.io/debug-adapter-protocol/specification)

[DAP client in neovim](https://github.com/mfussenegger/nvim-dap)

[DAP client in python](https://github.com/abhilashgupta/DAP-client/blob/master/Client_class.ipynb)

[Official DAP client reference](https://github.com/microsoft/debugpy/wiki/DAP-Client-reference)

[pydevd_reload](https://github.com/fyrestone/pydevd_reload)
