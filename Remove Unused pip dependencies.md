---
tags: [clean trash, python, remove unwanted, system  manage]
title: Remove Unused pip dependencies
created: '2022-08-04T03:58:57.701Z'
modified: '2022-08-18T16:21:08.007Z'
---

# Remove Unused pip dependencies

sometimes we install a single package which brings about tons of dependencies in python, `pip-autoremove` comes in handy.

install it by `pip3 install pip-autoremove`

though be careful these dependencies might not be used in other existing packages, they are sometimes still being used in your code!
