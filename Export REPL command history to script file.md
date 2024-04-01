---
title: Export REPL command history to script file
created: '2024-03-31T05:17:38.854Z'
modified: '2024-04-01T01:53:14.548Z'
---

# Export REPL command history to script file

general purpose terminal recorder:

```bash
script <record_filename>
```

to render the recorded file as plain text, run the following python script:

```python
import pyte

typescript_path = "mytypescript.log"
output_path = "typescript_plain.log"

# Specify the desired screen dimensions (columns x rows)
columns = 80 # please remember the columns for godsake.

# if you think it would be slow, use pypy instead.
rows = 100000 # what could go wrong now?

# Create a Screen object with the specified dimensions
screen = pyte.Screen(columns, rows)

# Create a ByteStream to handle ANSI control codes
stream = pyte.ByteStream(screen)

typescript_bytes = open(typescript_path,'rb').read()

# Insert ANSI control codes
stream.feed(typescript_bytes)

# Get the content with ANSI control codes
content = screen.display
plain_content ="\n".join(content).strip()

# Write the content to a file
with open(output_path, "w+") as file:
    file.write(plain_content)
```

---

for ipython one use `%history` for viewing history.

```python
# view current session history
%history
# write to file
%history -f ipython_output.log
# view all history across all sessions
%history -g
# view specific session history, like session 1
%history 1/
# for more, type the %quickref command and type /hist<Enter>
```

---

terminal jupyter notebook

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

---

metasploit history file location: `~/.msf4/history`

