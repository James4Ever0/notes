---
title: Export REPL command history to script file
created: '2024-03-31T05:17:38.854Z'
modified: '2024-03-31T16:08:30.927Z'
---

# Export REPL command history to script file

general purpose:

typescript

---

运行py的交互式命令行 如果想输出最近的操作 可以运行下面的代码

```python
# please define "history_output_path" beforehand

import readline

# Get the total number of history items in the current session
history_length = readline.get_current_history_length()

# Iterate over each history item and print the command
with open(history_output_path, 'w+') as f:
    for i in range(1, history_length + 1):
        item = readline.get_history_item(i)
        print(item)
        f.write(item+"\n")

```
---

Hackers are good at converting arbitrary actions into scripts.

At every step below we need file records.

```
Thoughs -> Actions -> Scripts -> Programs -> Systems
```

Human learn from trial and error, which is the origin of every good program, and REPL can be a better place than web based jupyter notebook. So we might want to find some command line alternative to jupyter.

Typically we need history, command output, filter out those errorneous commands, and save the output.

---

R has that functionality.

```r
# only current session history is keeped.
saveHistory("history.R")
# view history in popup
history()

```
