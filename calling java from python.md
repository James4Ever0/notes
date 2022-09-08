---
title: calling java from python
created: '2022-09-08T12:48:25.580Z'
modified: '2022-09-08T14:27:18.781Z'
---

# calling java from python

using [jpype](https://jpype.readthedocs.io/en/latest/userguide.html?highlight=jar#class-paths) or [pyjnius](https://github.com/kivy/pyjnius)

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

sample for pyjnius:

```python
import jnius_config
# jnius_config.add_options('-Xrs', '-Xmx4096')
jnius_config.set_classpath('.', "/root/Desktop/works/pyjom/tests/karaoke_effects/classpath/lingua.jar")
import jnius
jnius.autoclass('java.lang.System').out.println('Hello world')
detector = jnius.autoclass('com.github.pemistahl.lingua.api.LanguageDetectorBuilder').fromAllLanguages().build()

sample = 'hello world'

result = detector.detectLanguageOf(sample)
print(result, type(result))
# breakpoint()
strResult = result.toString()
print(strResult, type(strResult))
```
