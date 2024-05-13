---
title: FreeCAD Python Scripting
created: '2024-05-13T02:43:07.853Z'
modified: '2024-05-13T02:50:41.055Z'
---

# FreeCAD Python Scripting

Reference:

https://wiki.freecad.org/FreeCAD_Scripting_Basics

```python
import Part

doc = FreeCAD.ActiveDocument

# list all objects

all_objects = doc.Objects

# list all names

all_object_names = [it.Name for it in all_objects]

# get object by name

obj = doc.getObject("myObjectName")

# 
```
