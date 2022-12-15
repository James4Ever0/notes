---
title: useful java patterns
created: '2022-12-15T10:39:10.028Z'
modified: '2022-12-15T11:52:14.125Z'
---

# useful java patterns

learn java and kotlin the same time?

beanshell syntax highlight seems to be rare. beanshell workspace has the highlight.

use v2.1.1 and above for varargs support.

there are eclipse and [jetbrains](https://github.com/perNyfelt/beanshell-intellij-plugin) plugin support for beanshell.

creating lists:

```java
var a = new ArrayList<>(Arrays.asList(1,2,3));
var mset = new HashSet<>();
mset.addAll(a);
var mset2 = a.stream().collect(Collectors.toSet());

```

```kotlin
var a = arrayOf(1,2,3);
print(a.contentToString())
print(a.max())
print(a.min())
a.reverse()
```

