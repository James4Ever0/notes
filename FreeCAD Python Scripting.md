---
title: FreeCAD Python Scripting
created: '2024-05-13T02:43:07.853Z'
modified: '2024-05-13T06:09:44.793Z'
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

# recompute the document

doc.recompute()
```

Draw squares within specific bounds:

```python

margin = 15

# Define the dimensions of the square area
x_min = -210.134
x_max = -84.134
y_min = -140.0997
y_max = -14.0997
z = 0

# Define the number of squares in each row and column
num_squares = 10

# Calculate the side length of each square
x_length = (x_max - x_min) / num_squares
y_length = (y_max - y_min) / num_squares

# Create the squares
for i in range(num_squares):
    for j in range(num_squares):
        x_start = x_min + i * x_length + x_length / 10
        y_start = y_min + j * y_length + y_length / 10
        square_points = [
            App.Vector(x_start, y_start, z),
            App.Vector(x_start + x_length * 0.8, y_start, z),
            App.Vector(x_start + x_length * 0.8, y_start + y_length * 0.8, z),
            App.Vector(x_start, y_start + y_length * 0.8, z),
            App.Vector(x_start, y_start, z)
        ]
        Draft.makeWire(square_points, closed=True)

```
