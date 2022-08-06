---
created: 2022-08-07T02:38:53+08:00
modified: 2022-08-07T02:44:05+08:00
---

# Termux:Boot Autostart Program Fixes

according to [this](), termux:boot on android 10 and above will not work. instead, change all executables with relative paths in init scripts to their absolute paths. if any referred executable is a script file containing other executable with non-absolute paths(except for those built-in programs like am), change that too.
