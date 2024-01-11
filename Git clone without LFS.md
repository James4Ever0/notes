---
title: Git clone without LFS
created: '2024-01-11T17:35:30.242Z'
modified: '2024-01-11T17:36:36.296Z'
---

# Git clone without LFS

lfs download is mandatory while doing `git clone`

skip with:
```bash
env GIT_LFS_SKIP_SMUDGE=1 git clone --filter=blob:none <repo_url>
```
