---
title: useful java patterns
created: '2022-12-15T10:39:10.028Z'
modified: '2022-12-15T12:20:03.490Z'
---

# useful java patterns

learn java and kotlin the same time?

beanshell syntax highlight seems to be rare. beanshell workspace has the highlight.

use v2.1.1 and above for varargs support.

there are eclipse and [jetbrains](https://github.com/perNyfelt/beanshell-intellij-plugin) plugin support for beanshell.

## creating lists

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

## creating hashmap

```java
var ah= new HashMap<>();
ah.put(1,2);
```

```kotlin
var ah = hashMapOf(1 to 2, 2 to 3)
```

## iterate lists with indices

java double colon `::` operator acts as anonymous function

```java
var l = a.listIterator();
while (l.hasNext()){
  var index = l.nextIndex();
  var val = l.next();
  System.out.println("INDEX: "+index+" ELEM: "+val);
}

IntStream.range(0,a.size()).forEach(index -> a.get(index));

var index=0;
for (int i: a){
  index++;
}
```
```kotlin

a.forEachIndexed{ind, elem -> println("index? $ind"); println("elem? $elem")}

for (var i in a.indices){
  var elem = a[i]
}

a.indices.forEach {
  var elem = a[it]
  elem
}
```

## list comprehension
```java
var mlist = a.stream().map(x-> x*2).collect(Collectors.toList());
var evenNums = a.stream().filter(x-> x%2 == 0).collect(Collectors.toList());
var mmap = a.stream().collect(Collectors.toMap(x->x.getId(),x->x.getName()));
```


