---
title: filename issue on lexar m1
created: '2023-09-10T15:32:45.839Z'
modified: '2023-09-10T15:34:34.753Z'
---

# filename issue on lexar m1

this server forbids usage of leftperiod.

we can use [custom encoding rules](https://rclone.org/overview/#encoding) in rclone:

```bash
rclone sync --smb-encoding=Slash,LtGt,DoubleQuote,Colon,Question,Asterisk,Pipe,BackSlash,Ctl,RightSpace,RightPeriod,InvalidUtf8,Dot,LeftPeriod <source> <target>
```
