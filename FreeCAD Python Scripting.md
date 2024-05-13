---
title: FreeCAD Python Scripting
created: '2024-05-13T02:43:07.853Z'
modified: '2024-05-13T03:32:03.942Z'
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

# get vertex point

vertex_point = obj.Shape.Vertexes[0].Point

# create new line

new_line = Part.makeLine((-200, -200, 0), (200, 200, 0))

# insert the line

Part.show(new_line)
```
