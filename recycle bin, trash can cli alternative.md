---
title: 'recycle bin, trash can cli alternative'
created: '2023-08-19T18:09:18.216Z'
modified: '2023-08-20T01:47:06.484Z'
---

# recycle bin, trash can cli alternative

[trash-cli](https://github.com/sindresorhus/trash) (with [python binding](https://github.com/sindresorhus/trash-cli)) may work cross-platform, but manage its own recycle bin instead of the system if using windows or macos.

[empty-trash-cli](https://github.com/sindresorhus/empty-trash-cli)

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
# i don't trust this.
#rm -rf ~/.Trash/*

osascript -e 'tell app "Finder" to empty' 
```

[trash](https://hasseg.org/trash/)

rmtrash in [nightproductions's cli tools](http://www.nightproductions.net/cli.htm)
