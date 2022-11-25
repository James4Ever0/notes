---
created: 2022-11-25T21:29:13+08:00
modified: 2022-11-25T22:00:55+08:00
---

# hy lisp embedded in python, resumeable exception

hy缺乏基本的补全 vscode目前没法用 我把hy改造成了可以自动reload 自动抓Uncaught exception的模式 如果要取消这些行为 需要加上flag

```
-R
    disable automatic insertion of reloading decorator
-T
    disable toplevel try-except
-K
    disable toplevel show stacktrace
-L
    disable line-by-line try-except
```

一些未知的expression可能不允许被wrap到我们的macro里面 需要被加入到黑名单 已知的系列包括`unpack-iterable`之类的

hy的插件目前分为vim版本和EMACS版本 对spacevim spacemacs不怎么友好

hy的code autoindentation功能我做了 目前最新版本有待更新 主要是对字符串的正则进行了优化
