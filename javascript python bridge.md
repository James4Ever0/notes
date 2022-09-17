---
title: javascript python bridge
created: '2022-09-17T07:58:20.916Z'
modified: '2022-09-17T07:59:52.002Z'
---

# javascript python bridge

[jspybridge](https://github.com/extremeheat/JSPyBridge)

javascript in python:

```bash
pip3 install javascript
```

```python
from javascript import require, globalThis

chalk, fs = require("chalk"), require("fs")

print("Hello", chalk.red("world!"), "it's", globalThis.Date().toLocaleString())
fs.writeFileSync("HelloWorld.txt", "hi!")
```

access python from javascript:

```bash
npm i pythonia
```

```javascript
import { python } from 'pythonia'
// Import tkinter
const tk = await python('tkinter')
// All Python API access must be prefixed with await
const root = await tk.Tk()
// A function call with a $ suffix will treat the last argument as a kwarg dict
const a = await tk.Label$(root, { text: 'Hello World' })
await a.pack()
await root.mainloop()
python.exit() // Make sure to exit Python in the end to allow node to exit. You can also use process.exit.
```
