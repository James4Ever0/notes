---
tags: [cloud sync, git manage, repo manage, sync, system manage]
title: github Gitee 大文件大型repo如何上传
created: '2022-07-16T10:40:40.000Z'
modified: '2022-08-18T14:55:04.232Z'
---

# github Gitee 大文件大型repo如何上传

using github/gitee apis with watchdog.

exclude xonsh yaml(.yml) files

if you decide to upload the thing to github privately, and to sync among devices, then you need to deploy and share your ssh key.

run git related command after opened the vscode repeatedly, just like notable.

before git submodule .git folder deletion you may record the remote origin url to somewhere in the base folder.

you could patch the vscode launcher somehow, read the working directory to determine to repeatedly sync or not.

git init is a manual process.

also you might need five filelocks: one for main loop process running,  one for git sync, one for local sync, two for remote sync.

use `$@` or `$*` will do to pass arguments to the vscode binary.

首先不能follow symlink

其次忽略二进制文件 忽略特定后缀以外的文件

第一次建立的时候 递归扫描所有文件 去除大文件 append到.gitignore根目录下面

下一次 git add .之前 利用git的功能寻找有变化的文件目录 把大文件目录append到.gitignore里面
