---
title: 'recycle bin, trash can cli alternative'
created: '2023-08-19T18:09:18.216Z'
modified: '2023-08-20T01:41:50.669Z'
---

# recycle bin, trash can cli alternative

[trash-cli](https://github.com/sindresorhus/trash-cli) may work cross-platform, but manage its own recycle bin instead of the system if using windows or macos

## windows

[cmdutils](http://www.maddogsw.com/cmdutils/) which has `recycle` and `bin` commands

[cmd-recycle](https://github.com/kizzx2/cmd-recycle/)

[nircmd](http://www.nirsoft.net/utils/nircmd.html)

```cmd
nircmd moverecyclebin *.tmp
```

## macos

do this manually:

```bash
rm -rf ~/.Trash/*
```

[trash](https://hasseg.org/trash/)

rmtrash in [nightproductions's cli tools](http://www.nightproductions.net/cli.htm)

## linux
