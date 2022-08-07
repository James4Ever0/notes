---
title: MacOS locate fix and alternative
created: '2022-08-07T05:34:18.266Z'
modified: '2022-08-07T05:35:08.746Z'
---

# MacOS locate fix and alternative

## the fix

```bash
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist
```

## alternative

use `mdfind`
