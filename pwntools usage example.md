---
title: pwntools usage example
created: '2022-12-10T12:02:38.411Z'
modified: '2022-12-10T12:03:43.763Z'
---

# pwntools usage example

I created a script for solving a simple problem on RCTF.

```python
from pwn import *
ip = "190.92.234.114"
port = 23334

mclean =lambda l0: l0.decode().split("=")[1].strip()
mlist = lambda T: [int(x) for x in T.replace("[","").replace("]", "").replace(" ","").strip().split(",")]
r = remote(ip, port)
l0 = r.recvline()
# print('first line?', l0) # great man!
q = mclean(l0)
q = int(q)
# but notice you will not like to be fucked up. use safe eval? ast?
l1 = r.recvline()
# print('second line?', l1)
T = mclean(l1)
T = mlist(T)
l2 = r.recvline()
U = mlist(mclean(l2))
# print("third line?", l2)
print("Q?", q)
print()
print("T?", len(T))
print()
print("U?", len(U))

# now crack the x. please observe the original code?

# the shift does not matter so much?

mpos_x = {}
for i in range(90):
    t = T[i]
    u = U[i]
    pos_x = u//t+1
    mpos_x.update({pos_x:mpos_x.get(pos_x,0)+1})

mfinalPos = [(key, elem) for key, elem in mpos_x.items()]
mfinalPos.sort(key=lambda x: -x[1])
print("NUM?",mfinalPos[0])
print("COUNT?",mfinalPos[0][1])
# import pyperclip
data =str(mfinalPos[0][0])
# pyperclip.copy(data)
# r.interactive()
r.sendline(data.encode())
flag=r.recvline() #EOFERROR?
print("FLAG?",flag)
# now answer the shit?
```
