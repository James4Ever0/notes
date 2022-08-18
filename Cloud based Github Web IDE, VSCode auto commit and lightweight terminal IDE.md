---
tags: [agile editing, cloud IDE, devops, sync]
title: 'Cloud based Github Web IDE, VSCode auto commit and lightweight terminal IDE'
created: '2022-07-21T14:02:12.000Z'
modified: '2022-08-18T14:14:22.409Z'
---

# Cloud based Github Web IDE, VSCode auto commit and lightweight terminal IDE

solved by gitfs

libgit2 sucks.

[most stars](https://github.com/presslabs/gitfs)
this gitfs is actually a searchable git history filesystem.

[tested](https://github.com/semk/GitFS)

[gitee python api, first step is to get access token by login](https://gitee.com/wuyu15255872976/gitee-python-client/tree/master/gitee_client/apis)

[gitee apis](https://gitee.com/api/v5/swagger#/postV5ReposOwnerRepoContentsPath)

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
