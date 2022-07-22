---
title: Cloud based Github Web IDE, VSCode auto commit and lightweight terminal IDE
created: 2022-07-21T22:02:12+08:00
modified: 2022-07-22T11:09:47+08:00
---

# Cloud based Github Web IDE, VSCode auto commit and lightweight terminal IDE

can we mount git/github repo as user filesystem(fuse)?

usually read-only github/git filesystems, but this one is different. [it](https://github.com/danishprakash/githubfs) is backed by [writable github apis](https://pygithub.readthedocs.io/en/latest/examples/Repository.html#update-a-file-in-the-repository) and is written in python, with [python implementation of fuse](https://github.com/terencehonles/fusepy) which is updated [here](https://github.com/fusepy/fusepy). this pygithub has trending api(maybe?) which is useful for social engineering or propaganda.

we could also implement a watchdog like system to check against the files using pygithub.

cloud based github ide includes gitpod.io, github.dev, pythonanywhere but these are with serious limitations, most importantly without autocommit or too restricted to write code.

browse github repo as remote filesystem(vscode insider):
https://marketplace.visualstudio.com/items?itemName=github.remotehub

the vscode desktop is too resource heavy. though we have found [a plugin to auto commit](https://marketplace.visualstudio.com/items?itemName=emjio.git-auto-commit) that also has [a github repo](https://github.com/emjio/git-auto-commit) to git repo(only for vscode insider):

spacevim with [custom color theme](https://github.com/jordst/colorscheme) and nerdfont installed.

[spacevim documentation](https://spacevim.org/documentation/)

[vim wiki by fandom](https://vim.fandom.com/wiki)

run multiple vim commands at once:
```vimscript
:cd / | NERDTree
```
