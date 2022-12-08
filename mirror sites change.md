---
title: mirror sites change
created: '2022-12-06T14:37:42.715Z'
modified: '2022-12-08T17:55:31.307Z'
---

# mirror sites change

if it only blocks a range of ip, you use proxy to avoid this constraint.

some mirror sites serves us poorly and block access from us. we point them out, list alternatives and provide quick fixes.

these actions are intentionally done against specific group of people. it does block a whole range of IPs.

actors:

```
https://mirrors.aliyun.com
https://mirrors.tuna.tsinghua.edu.cn/
```

fixes:

currently we use some previously picked up tunnel accounts provided by topsap. may fix this problem?

python pip:
```bash
pip3 config set global.index-url https://mirrors.ustc.edu.cn/pypi/web/simple
```

taobao npm mirror:
```
http://npm.taobao.org => http://npmmirror.com
http://registry.npm.taobao.org => http://registry.npmmirror.com
```
