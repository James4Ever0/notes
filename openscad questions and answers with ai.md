---
created: 2026-01-05T10:01:59+08:00
modified: 2026-01-05T10:04:41+08:00
---

# openscad questions and answers with ai

User:

how to assign an object to a variable.
d = cube(15, center=true); does not work in openscad.

Bot:

In OpenSCAD, you **cannot** assign geometry objects (like cubes, spheres, etc.) to variables directly. OpenSCAD works differently from imperative programming languages.

Here's how you should work with objects in OpenSCAD:

## Correct Approach: Define a **Module**
```openscad
module my_cube() {
    cube(15, center=true);
}

// Usage
my_cube();
```

## Or use variables for **parameters only**:
```openscad
cube_size = 15;
cube_position = [0, 0, 0];

// Create the cube with parameters
translate(cube_position)
    cube(cube_size, center=true);
```

## If you need "objects" with transformations:
```openscad
module create_cube(size, position) {
    translate(position)
        cube(size, center=true);
}

// Create instances
create_cube(15, [0, 0, 0]);
create_cube(15, [20, 0, 0]);  // Another cube
```

## Key Points:
1. **Modules** are OpenSCAD's way of creating reusable objects
2. Variables can only store simple values (numbers, strings, booleans, lists)
3. Geometry creation (like `cube()`, `sphere()`) must be at the top level or inside a module
4. OpenSCAD is a **declarative language** - you describe what you want, not step-by-step instructions

## Workaround for multiple references:
If you need to use the same geometry in multiple places:
```openscad
module basic_shape() {
    cube(15, center=true);
    sphere(10);
}

// Use it multiple times
basic_shape();
translate([30, 0, 0]) basic_shape();
```

This is different from languages like Python or JavaScript, but it's how OpenSCAD's rendering engine works - everything gets compiled to a final geometry tree.

User:

what is the difference between openscad module and function

Bot:

In OpenSCAD, **modules** and **functions** serve different purposes:

## **Functions**
Functions **calculate and return values** (numbers, strings, booleans, vectors/lists).
```openscad
// Function: Returns a value
function calculate_volume(r) = 4/3 * 3.14159 * r * r * r;

// Usage: Store return value in variable
sphere_volume = calculate_volume(10);
echo(sphere_volume); // Output: 4188.79

// Functions can return vectors
function create_point(x, y, z) = [x, y, z];
point = create_point(10, 20, 30);
```

**Functions CANNOT:**
- Create geometry (no `cube()`, `sphere()`, etc.)
- Use transformations (no `translate()`, `rotate()`, etc.)
- Have multiple statements (usually single expression)

## **Modules**
Modules **create geometry** and can include transformations.
```openscad
// Module: Creates geometry
module create_sphere(r) {
    sphere(r);
}

// Usage: Creates actual 3D object
create_sphere(10);

// Modules can include transformations
module positioned_cube(size, pos) {
    translate(pos)
        cube(size, center=true);
}
```

## **Key Differences Table**

| Feature | **Function** | **Module** |
|---------|-------------|------------|
| **Returns value** | Yes (single value) | No |
| **Creates geometry** | No | Yes |
| **Can use transformations** | No | Yes |
| **Can assign to variable** | Yes (the return value) | No |
| **Multiple statements** | Limited (let/if) | Yes |
| **Example** | `function add(a,b)=a+b;` | `module box() { cube(10); }` |

## **Practical Example**
```openscad
// Function calculates a value
function circle_area(r) = PI * r * r;

// Module creates geometry
module ring(inner_r, outer_r) {
    difference() {
        circle(outer_r);
        circle(inner_r);
    }
}

// Use function to calculate
area = circle_area(5);
echo("Area:", area);

// Use module to create geometry
ring(3, 5);
```

## **When to Use Each**
- **Use functions** for calculations, math, generating data
- **Use modules** for creating shapes, parts, assemblies

## **Important Limitation**
You cannot do this:
```openscad
// WRONG - Can't assign geometry to variable
my_shape = cube(10);  // Error!

// CORRECT - Create a module
module my_shape() {
    cube(10);
}
my_shape();  // Create the geometry
```

OpenSCAD is a **declarative language** - you describe the final 3D model, not step through instructions. Modules describe shapes, functions describe calculations.

User:

can i create two parallel 2d shapes on different x-y planes with different z height, and connect the two planes somehow by "extrusion"

Bot:

Yes! OpenSCAD has several ways to connect 2D shapes on different planes. Here are the main methods:

## **1. Linear Extrusion with `linear_extrude()`**
For extruding a single 2D shape vertically:
```openscad
// Extrude a 2D shape to 3D
linear_extrude(height = 10) {
    square(20, center=true);
}
```

## **2. Hull Connection**
Use `hull()` to create a convex hull between shapes:
```openscad
// Connect two shapes with a convex hull
hull() {
    // Bottom shape at z=0
    translate([0, 0, 0])
        circle(10);

    // Top shape at z=20
    translate([0, 0, 20])
        circle(5);
}
```

## **3. Manual Connection with Polyhedron**
For precise control between shapes with different numbers of vertices:
```openscad
// Create a tube between two circles
bottom_points = [[0,0], [10,0], [0,10], [-10,0], [0,-10]];
top_points = [[0,0], [5,0], [0,5], [-5,0], [0,-5]];

polyhedron(
    points = [
        for(p = bottom_points) [p[0], p[1], 0],    // Bottom at z=0
        for(p = top_points) [p[0], p[1], 20]       // Top at z=20
    ],
    faces = [
        // Bottom face (counter-clockwise)
        [0, 1, 2, 3, 4],
        // Top face (clockwise)
        [9, 8, 7, 6, 5],
        // Side faces
        [0, 5, 6, 1],
        [1, 6, 7, 2],
        [2, 7, 8, 3],
        [3, 8, 9, 4],
        [4, 9, 5, 0]
    ]
);
```

## **4. Skin/loft Function (Advanced)**
Create a function to "skin" between multiple cross-sections:
```openscad
module skin(profiles, heights) {
    for(i = [0 : len(profiles)-2]) {
        hull() {
            translate([0, 0, heights[i]])
                linear_extrude(0.01)
                    polygon(profiles[i]);
            translate([0, 0, heights[i+1]])
                linear_extrude(0.01)
                    polygon(profiles[i+1]);
        }
    }
}

// Define profiles (arrays of points)
bottom_profile = [[-10,-10], [10,-10], [10,10], [-10,10]];
top_profile = [[-5,-5], [5,-5], [5,5], [-5,5]];

skin([bottom_profile, top_profile], [0, 20]);
```

## **5. Minkowski with Thin Extrusions**
Create smooth transitions:
```openscad
// Create a smooth transition shape
minkowski() {
    hull() {
        translate([0, 0, 0])
            linear_extrude(0.1)
                circle(10);
        translate([0, 0, 20])
            linear_extrude(0.1)
                circle(5);
    }
    sphere(1);  // Rounds the edges
}
```

## **6. Practical Example: Tapered Tube**
```openscad
difference() {
    // Outer shape
    hull() {
        translate([0, 0, 0])
            cylinder(h=0.1, r=15);
        translate([0, 0, 30])
            cylinder(h=0.1, r=10);
    }

    // Inner shape (cutout)
    hull() {
        translate([0, 0, -0.1])
            cylinder(h=0.2, r=12);
        translate([0, 0, 30.1])
            cylinder(h=0.2, r=7);
    }
}
```

## **Tips:**
1. **`hull()`** is simplest but creates convex shapes only
2. **`polyhedron()`** gives most control but needs manual vertex/face definition
3. Ensure shapes have same number of vertices for clean connections
4. Use `linear_extrude()` with twist/scale for helical or tapered extrusions

## **For Complex Shapes:**
Consider the BOSL2 library which has a `skin()` module:
```openscad
use <BOSL2/std.scad>

skin([
    circle(10),
    circle(5)
], z=[0, 20]);
```

**Which method to choose?**
- Use `hull()` for simple convex connections
- Use `polyhedron()` for precise control
- Use BOSL2 library for complex lofting operations
-
