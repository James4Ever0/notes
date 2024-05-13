---
title: FreeCAD Python Scripting
created: '2024-05-13T02:43:07.853Z'
modified: '2024-05-13T06:37:54.104Z'
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
x_min = -210.134 + margin
x_max = -84.134 - margin
y_min = -140.0997 + margin
y_max = -14.0997 - margin
z = 0

# Define the number of squares in each row and column
num_squares = 10

# Calculate the side length of each square
x_length = (x_max - x_min) / num_squares
y_length = (y_max - y_min) / num_squares

margin_portion = 0.17
hole_portion = 1 - 2 * margin_portion

# Create the squares
for i in range(num_squares):
    for j in range(num_squares):
        x_start = x_min + i * x_length + x_length * margin_portion
        y_start = y_min + j * y_length + y_length * margin_portion
        square_points = [
            (x_start, y_start, z),
            (x_start + x_length * hole_portion, y_start, z),
            (x_start + x_length * hole_portion, y_start + y_length * hole_portion, z),
            (x_start, y_start + y_length * hole_portion, z),
            (x_start, y_start, z), # to make it closed
        ]
        square = Part.makePolygon(square_points)
        Part.show(square)

```

Draw circles with specific bounds:

```python
margin = 15

# Define the dimensions of the square area
x_min = -210.134 + margin
x_max = -84.134 - margin
y_min = -140.0997 + margin
y_max = -14.0997 - margin
z = 0

# Define the number of circles in each row and column
num_circles = 10

# Calculate the side length of each circle
x_length = (x_max - x_min) / num_circles
y_length = (y_max - y_min) / num_circles

margin_portion = 0.17
radius_portion = 0.5 - margin_portion
radius = x_length * radius_portion

direction = (0, 0, 1)

# Create the squares
for i in range(num_circles):
    for j in range(num_circles):
        x_center = x_min + i * x_length + x_length * 0.5
        y_center = y_min + j * y_length + y_length * 0.5
        circle = Part.makeCircle(radius, (x_center, y_center, 0), direction)
        Part.show(circle)

```
