---
title: github Gitee 大文件大型repo如何上传
created: '2022-07-16T10:40:40.000Z'
modified: '2022-07-16T14:55:28.661Z'
---

# github Gitee 大文件大型repo如何上传

run git related command after opened the vscode repeatedly, just like notable.

you could patch the vscode launcher somehow, read the working directory to determine to repeatedly sync or not.

首先不能follow symlink

其次忽略二进制文件 忽略特定后缀以外的文件

第一次建立的时候 递归扫描所有文件 去除大文件 append到.gitignore根目录下面

下一次 git add .之前 利用git的功能寻找有变化的文件目录 把大文件目录append到.gitignore里面
