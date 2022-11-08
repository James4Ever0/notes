---
title: Remove bad/large files from git repo history
created: '2022-11-08T16:24:06.896Z'
modified: '2022-11-08T16:38:12.888Z'
---

# Remove bad/large files from git repo history

[remove sensitive data from github](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

use [bfg repo cleaner](https://rtyley.github.io/bfg-repo-cleaner/), avaliable in `brew`, downloadable [as a jar](https://repo1.maven.org/maven2/com/madgag/bfg/1.14.0/bfg-1.14.0.jar).

[git-filter-repo](https://github.com/newren/git-filter-repo#solving-this-with-bfg-repo-cleaner)

other tools either perform poorly or have complex syntax. may not work as expected!

[cheat sheet for converting bfg commands into git filter-repo](https://github.com/newren/git-filter-repo/blob/main/Documentation/converting-from-bfg-repo-cleaner.md#cheat-sheet-conversion-of-examples-from-bfg)
