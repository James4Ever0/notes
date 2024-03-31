---
title: Export REPL command history to script file
created: '2024-03-31T05:17:38.854Z'
modified: '2024-03-31T05:26:08.321Z'
---

# Export REPL command history to script file

Hackers are good at converting arbitrary actions into scripts.

The program follows:

```
Thoughs -> Actions -> Scripts -> Programs
```

Human learn from trial and error, which is the origin of every good program, and REPL can be a better place than web based jupyter notebook. So we might want to find some command line alternative to jupyter.

Typically we need history, command output, filter out those errorneous commands, and save the output.

R has that functionality.
