---
title: useful java patterns
created: '2022-12-15T10:39:10.028Z'
modified: '2022-12-15T13:18:35.353Z'
---

# useful java patterns

[java stream guide](https://stackify.com/streams-guide-java-8/)

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
var mymin = Collections.min(a);
var mymax = Collections.max(a);
Collections.reverse(a);
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

## switch expressions

```java
var val = 2;
var mswitch = switch (val){
  case 1,2,3 -> {
    yield "good";
  }
  case 4,5,6 -> {
    yield "bad";
  } // either throw or yield.
  default -> {
    System.out.println("out of expectation");
    yield "really bad";
  }
};
System.out.println(mswitch);
```

```kotlin
var grade = 30
var res =  when(grade) {
        in 0..40 -> "Fail"
        in 41..70 -> "Pass"
        in 71..100 -> "Distinction"
        else -> false
    }
print(res)

var mcase = 1
var res = when(mcase){
  1 -> "good"
  2 -> "bad"
  else -> "really bad"
}
print(res)
```

### count occurance of elements in array

```java
String[] array = {"name1","name2","name3","name4", "name5", "name2"};
Arrays.stream(array)
      .collect(Collectors.groupingBy(s -> s))
      .forEach((k, v) -> System.out.println(k+" "+v.size()));

List asList = Arrays.asList(array);
Set<String> mySet = new HashSet<String>(asList);

for(String s: mySet){
 System.out.println(s + " " + Collections.frequency(asList,s));
}

Map<String, Long> map = Arrays.stream(array)
    .collect(Collectors.groupingBy(s -> s, Collectors.counting()));
```

```kotlin
var a = arrayOf(1,2,3,3,3,3)

a.toSet().forEach{it -> println("elem? $it"); println("count? "+a.count{it2->it2 == it})}
```

### lambdas

```java
Consumer mcons = (n) -> {System.out.println(n);}
mcons.andThen(mcons).accept("mval");
Function <Integer,Integer> mfunc = n-> n+1;
Supplier msup = () -> 1;
var mval = msup.get();
```

```kotlin
var mfunc = {n :Int -> n+1}
var mprint = {n:Any -> print(n)}
```
