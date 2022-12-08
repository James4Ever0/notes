---
title: nctf writeups
created: 2022-12-05T08:00:02+00:00
modified: 2022-12-08T17:14:02+08:00
---

# nctf writeups

## challenges

[the platform](https://nctf.h4ck.fun)

[official released source code](https://github.com/X1cT34m/NCTF2022)

[buuctf](https://buuoj.cn/) online judge

you may find many writeups [in blog](https://oopsdc.com/post/buuctf/) and [github](https://github.com/Yeuoly/buuctf_pwn) for buuctf.

## hints and tools

binwalk

[arr3esty0u github info](https://github.com/Arr3stY0u)

[shg-sec](https://shg-sec.com/#)

[hack.lu 2022](https://ctftime.org/event/1727)

ayacms rce in nctf 2022? how to identify the cms? and how the fuck did those guys identify the shit from that damn website (bing-upms)?

answer: they are both busting common web directories. can be induced by common repo structures.

[baby-aes](https://github.com/zieglerk/baby-AES) for crypto signin?

[zsteg](https://www.doyler.net/security-not-included/zsteg-easy-ctf-flags) for solving that png problem?

[normal sql injection, not for denodb](https://www.doyler.net/security-not-included/sqlite-injection)

[huli: interesting blog where denodb 0day came from](https://blog.huli.tw)

some z3 code, which does not but angr solved the problem

```python
from z3 import *
data1=0x162AEB99F80DD8EF8C82AFADBA2E087A
data2=0x47C9F2ACA92F6476BE7F0A6DC89F4305
data3=0x33B57575
answer=[]
flag1=[]
key=[0x7e,0x1f,0x19,0x75]
solver=Solver()
flag=[Int('flag%d'%i) for i in range(36)]
for i in range(16):
    answer.append((data1>>8*i)&0xff)
for i in range(16):
    answer.append((data2>>8*i)&0xff)
for i in range(4):
    answer.append((data3>>8*i)&0xff)
print(answer)
for i in range(0,9):
    v3=key[3]
    v4=flag[4*i+3]
    v5=key[0]
    v6=flag[4*i]
    v7=flag[4*i+1]
    v8=key[1]
    v9=flag[4*i+2]
    v10=(v6 + v4) * (key[0] + v3)
    v11=key[2]
    v12 = v3 * (v6 + v7)
    v13 = (v3 + v11) * (v7 - v4)
    v14 = v4 * (v11 - v5)
    v15 = v5 * (v9 + v4)
    solver.add(v14+v10+v13-v12==answer[4*i])
    solver.add(v6 * (v8 - v3) + v12==answer[4*i+1])
    solver.add(v15 + v14==answer[4*i+2])
    solver.add(v6 * (v8 - v3) + (v8 + v5) * (v9 - v6) + v10 - v15==answer[4*i+3])

if solver.check()==sat:
    m=solver.model()
    rex = []
    for i in range(34):
        rex.append(m[flag[i]].as_long())
    print(rex)
else:
    print("n0")
```

## writeups

[saying this is complete for 2022 nctf?](https://pupil857.github.io/)

[arr3ty0u nctf 2022 writeup](http://mp.weixin.qq.com/s?__biz=Mzg4MjcxMTAwMQ==&mid=2247485772&idx=1&sn=0f5b969f111d79027c59e6e2145698ef&chksm=cf53c9faf82440ec839aa7fc6b35bbc03251c824c5c5407ed9eb51181471d7514d651e3cfe97&mpshare=1&scene=23&srcid=12055uACFGja8KBjcPtP8ErG&sharer_sharetime=1670169963855&sharer_shareid=6eea79ff6da57fc6752ab0bc570bf392#rd)

[nctf 2019 writeup](https://www.codetd.com/en/article/9046407)

don't know when it is, but i remember i have seen this shit: [katastros's nctf writeup](https://blog.katastros.com/a?ID=00650-571829f2-3af9-4b1c-a3b7-3ebebca04377)

[ctfiot chamd5 nctf 2022 writeup](https://www.ctfiot.com/83703.html)

[nctf 2022 official crypto writeup](http://blog.tolinchan.xyz/2022/12/05/nctf-2022-official-writeup-crypto/)
