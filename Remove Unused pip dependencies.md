---
title: Remove Unused pip dependencies
created: '2022-08-04T03:58:57.701Z'
modified: '2022-08-04T04:00:55.194Z'
---

# Remove Unused pip dependencies

sometimes we install a single package which brings about tons of dependencies in python, `pip-autoremove` comes in handy.

install it by `pip3 install pip-autoremove`

though be careful these dependencies might not be used in other existing packages, it is sometimes still being used in your code!
