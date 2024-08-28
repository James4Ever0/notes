---
created: 2024-08-28T22:50:33+08:00
modified: 2024-08-28T22:51:39+08:00
---

# Typing training

Linux:

```python
import random
import traceback

import tty
import sys
import os

tty.setcbreak(sys.stdin)
window = 5


def truth():
    payload = "abcdefghijklmnopqrstuvwxyz"
    payload += payload.upper()
    payload += "0123456789"
    payload += "~_+{}|:`-=[]\\;!@#$%^&*()'\"<>/?"
    payload = [x for x in payload]
    return "".join(random.sample(payload, 9))


while True:
    try:
        r = truth()
        fst = r
        nxt = r
        r1 = ""
        for r0 in nxt:
            t = True
            while t:
                os.system("clear")
                print("question:", fst)
                print("slider:", r1)
                print("answer:")
                ans = sys.stdin.read(1)
                if ans == r0:
                    print("correct!")
                    r1 += r0
                    t = False
                else:
                    print("incorrect!")
                    print("the correct answer is:", r0)
                    print("your answer is:", ans)
        print("correct form:", r)
        print("continue?")
        input()
    except:
        traceback.print_exc()
        print("exception printed above!")
        pass
```
