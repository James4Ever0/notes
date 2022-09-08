---
title: calling java from python
created: '2022-09-08T12:48:25.580Z'
modified: '2022-09-08T13:40:58.540Z'
---

# calling java from python

using [jpype](https://jpype.readthedocs.io/en/latest/userguide.html?highlight=jar#class-paths)

sample code for jpype:

```python
from jpype import *
import jpype.imports # this is needed! shit.

addClassPath("/root/Desktop/works/pyjom/tests/karaoke_effects/classpath/lingua.jar")

startJVM(getDefaultJVMPath())
java.lang.System.out.println("Calling Java Print from Python using Jpype!")

from com.github.pemistahl.lingua.api import *


# detector = LanguageDetectorBuilder.fromAllLanguages().withLowAccuracyMode().build()
detector = LanguageDetectorBuilder.fromAllLanguages().build() # 3.5GB just for detecting language! it is somehow crazy.

sample = 'hello world'

result = detector.detectLanguageOf(sample)
print(result, type(result)) # <java class 'com.github.pemistahl.lingua.api.Language'>
# but we can convert it into string.
strResult = str(result)
print(strResult, type(strResult))
import math

print("CALLING MATH: %d" % math.sqrt(4))
shutdownJVM()
```
