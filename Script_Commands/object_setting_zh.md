---
title: 对象设置
description: This section introduces the functions that can be used to add and manipulate objects such as structures, sources, monitors, groups, material, and variables.
keywords: Set object,Add object,Manipulate structures,Select plane sources,Add index monitors,Add analysis groups,Set material,Add rectangle,Add mode port
businessId: Script-Commands_setting-objects
language: zh-CN
sort: 22
published: true
date: 2024-03-04T07:18:09.531Z
tags: objectsetting
editor: markdown
dateCreated: 2022-06-14T08:40:47.121Z
---


**This section introduces the functions that can be used to add and manipulate objects such as structures, sources, monitors, groups, materials, and variables.**


# Structure

## addpoly
**Description**
Adds a polygon structure to the simulation environment according to the current view plane in the composite  viewer window.
For example, if the current view plane is ZX plane, `addpoly` function will constitute a polygon in ZX plane using a set of z, x coordinates called vertices and extrude it along the y direction.
Used in FDTD and FDE.


**Syntax**
|Code|Function|
|:---|:---|
|`addpoly;`|Adds a polygon structure according to the current view plane in the composite window.|
|`addpoly(x_pos, y_pos, z_pos);`|Adds a polygon structure with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) according to the current view plane in the composite viewer window.|

**Example**
Switch to the ZX view, then run the following script to create a 3D polygon with the specified vertices decided by matrix "vers".

```msf
vers = [0,2;2,4;4,3;2.5,1]*1e-6; # unit: m
addpoly;
set("name", "new_polygon");
set("vertices", vers);
set("y span", 3e-6);
```
**See also**
set, add2dpolygon

## addrect
**Description**
Adds a rectangle structure to the simulation environment.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addrect;`|Adds a rectangle structure to the simulation environment.|
|`addrect(x_pos, y_pos, z_pos);`|Adds a rectangle structure to the simulation environment with designated center position *x_pos*, *y_pos*, and *z_pos*(unit: m).|


**Example**
The following script creates a rectangle structure with designated dimension and material at  specified position.

```msf
addrect;                          # add a rectangle to the simulation environment
set("name", "new_rectangle");      # set the name of rectangle

# set the dimension and center position of rectangle
set("x", 0);        # unit: m
set("x span", 6e-6);
set("y", 1e-6);
set("y span", 2e-6);
set("z", 0);
set("z span", 3e-6);

# set the material of rectangle
set("material", "Ag (Silver)_CRC");  
```


**See also**
set, add2drect

## addtriangle
**Description**
Adds a triangle structure which can be seen as a 3 vertex, triangle shaped polygon to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addtriangle` function will constitute a triangle  in ZX plane using a set of three z, x coordinates called vertices and extrude it along the y direction.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addtriangle;`|Adds a triangle structure to the simulation environment.|
|`addtriangle(x_pos, y_pos, z_pos);`|Adds a triangle structure to the simulation environment with designated center position *x_pos*, *y_pos*, and *z_pos*(unit: m).|

**Example**
Switch to the ZX view, then run the following script to create a triangle with the specified vertices decided by matrix "trg".

```msf
trg = [1,0;2,2;4,0]*1e-6;  # to store the coordinates of three corners of triangle, unit: m

addtriangle;
set("name", "new_triangle"); 
set("vertices", trg);
set("y span", 6e-6);  # unit: m
```

**See also**
set, addpoly

## addellipse
**Description**
Adds an ellipse structure to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addellipse` function will constitute an ellipse in ZX plane and extrude it along the y direction.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addellipse;`|Adds an ellipse structure to the simulation environment.|
|`addellipse(x_pos, y_pos, z_pos);`|Adds an ellipse structure to the simulation environment with designated center position *x_pos*, *y_pos*, and *z_pos*(unit: m).|

**Example**

Create an ellipse structure, then set its radius to 1 um and radius 2 to 0.5 um.
```msf
addellipse;              # create ellipse structure
set('radius', 1e-6);     # set radius to 1 um
set('radius 2', 0.5e-6); # set radius 2 to 0.5 um

```
**See also**
set, addcircle


## addcircle
**Description**
Adds a circle structure to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addcircle` function will constitute a circle in ZX plane and extrude it along the y direction.
Used in FDTD and FDE.


**Syntax**
|Code|Function |
|:---|:---|
|`addcircle;`|Adds a circle structure to the simulation environment according to the current view plane in the composite viewer window.|
|`addcircle(x_pos, y_pos, z_pos)`|Adds a circle structure to the simulation environment with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) according to the current view plane in the composite viewer window.|

**Example**
Create a circle structure, then set its radius to 1 um.
```msf
addcircle;
set('radius', 1e-6); # set radius to 1 um

```
**See also**
set, addellipse

## addsector
**Description**
Adds a sector structure which can be seen as part of a circle structure to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addsector` function will constitute a sector in ZX plane and extrude it along the y direction.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addsector;`|Adds a sector structure to the simulation environment according to the current view plane in the composite viewer window.|
|`addsector(x_pos, y_pos, z_pos);`|Adds a sector structure with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment according to the current view plane in the composite viewer window.|


**Example**
Create a sector structure, then set its radius, start angle, and angle span.
```msf
addsector;
set('radius', 1e-6);   # unit: m
set('start angle', 0); # unit: degree
set('span angle', 90);

```
**See also**
set, addcircle

## addcirclering
**Description**
Adds a circular ring structure to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addcirclering` function will constitute a circular ring in ZX plane and extrude it along the y direction.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addcirclering;`|Adds a circular ring structure to the simulation environment according to the current view plane in the composite viewer window.|
|`addcirclering(x_pos, y_pos, z_pos);`|Adds a circular ring structure with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment according to the current view plane in the composite viewer window.|


**Example**
Create a circular ring, then set its (outer) radius and width.

```msf
addcirclering;
set('radius', 2e-6);  # outer radius (m)
set('width', 1.5e-6); # width (m)
```

**See also**
set, addellipsering

## addellipsering
**Description**
Adds an elliptic ring structure to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addellipsering` function will constitute an elliptic ring in ZX plane and extrude it along the y direction.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addellipsering;`|Adds an elliptic ring structure to the simulation environment according to the current view plane in the composite viewer window.|
|`addellipsering(x_pos, y_pos, z_pos);`|Adds an elliptic ring structure with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment according to the current view plane in the composite viewer window.|

**Example**
Create an elliptic ring, then set its radius (m), radius 2 (m) and width (m).

```msf
addellipsering;
set('radius', 2e-6);    # unit: m
set('radius 2', 1e-6);
set('width', 8e-7);
```

**See also**
set, addcirclering

## addsphere
**Description**
Adds a sphere structure to the simulation environment.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addsphere;`|Adds a sphere structure to the simulation environment.|


**Example**
Example 1 : Create a sphere, then set its radius (m).
```msf
addsphere;
set('radius', 2e-6);    # unit: m
```
Example 2 : Create an ellipsoidal sphere with different radius in x, y, z direction.
```msf
addsphere;
set('make ellipse', 1);
set('radius', 1e-6);    # unit: m
set('radius 2', 2e-6);
set('radius 3', 3e-6);
```

**See also**
set, addcircle

## addpyramid
**Description**
Adds a pyramid structure to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addpyramid` function will constitute a pyramid whose bottom is perpendicular to Y axis.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addpyramid;`|Adds a pyramid structure to the simulation environment according to the current view plane in the composite viewer window.|
|`addpyramid(x_pos, y_pos, z_pos);`|Adds a pyramid structure with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment according to the current view plane in the composite viewer window.|

**Example**
Switch to ZX view. Create a pyramid, then set its top dimension, bottom dimension and height(y span).

```msf
addpyramid;

# set top and bottom dimension
set('name', 'new_pyramid');
set('top z span', 1e-6);    # unit: m
set('top x span', 1.2e-6);
set('bottom z span', 2e-6);
set('bottom x span', 2.4e-6);

# set height
set('y span', 2.7e-6);

```

**See also**
set, addcone

## addcone
**Description**
Adds a cone structure to the simulation according the current view plane in the composite viewer window.
For example, if the current view plane is  ZX plane, `addcone` function will constitute a cone whose bottom is perpendicular to Y axis.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addcone;`|Adds a cone structure to the simulation environment according to the current view plane in the composite viewer window.|
|`addcone(x_pos, y_pos, z_pos);`|Adds a cone structure with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment according to the current view plane in the composite viewer window.|

**Example**
Switch to ZX view. Create a cone, then set its top dimension, bottom dimension and height.
```msf
addcone;

# set top and bottom dimension
set('name', 'new_cone');
set('top make ellipse', 1);
set('top radius', 1e-6);    # unit: m
set('top radius 2', 2e-6);
set('bottom make ellipse', 1);
set('bottom radius', 2e-6);
set('bottom radius 2', 4e-6);

# set height
set('y span', 2.7e-6);
```

**See also**
set, addpyramid


## addlinearwaveguide
**Description**
Adds a linear waveguide to the simulation environment according to the current view plane in the composite viewer window.
Used in FDTD and FDE.

**Syntax**
|Code|Function |
|:---|:---|
|`addlinearwaveguide;`|Adds a linear waveguide to the simulation environment according to the current view plane in the composite viewer window. |

**See also**
addarcwaveguide


## addarcwaveguide
**Description**
Adds a curved waveguide to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addarcwaveguide` function will constitute a partial ring in ZX plane and extrude it along the y direction.
Used in FDTD and FDE.

**Syntax**
|Code|Function |
|:---|:---|
|`addarcwaveguide;`|Adds a curved waveguide to the simulation environment according to the current view plane in the composite viewer window.|


**See also**
addlinearwaveguide


## addlineartaper
**Description**
Adds a linear taper structure to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is  ZX plane, `addlineartaper` function will constitute a trapezium in ZX plane and extrude it along the y direction.
Used in FDTD and FDE.

**Syntax**
|Code|Function |
|:---|:---|
|`addlineartaper;`|Adds a linear taper structure to the simulation environment according to the current view plane in the composite viewer window.|


**See also**
addlinearwaveguide

## addsidewalllinear
**Description**
Adds a linear structure with two sidewalls tilted at a specific angle to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is  ZX plane, `addsidewalllinear` function will constitute a taper structure whose top and bottom are parallel to the ZX plane.  
Used in FDTD and FDE.

**Syntax**
|Code|Function |
|:---|:---|
|`addsidewalllinear;`|Adds a linear structure  with two slanted sidewalls to the simulation environment according to the current view plane in the composite viewer window.|


**See also**
addlinearwaveguide, addlineartaper


## addsidewallarc
**Description**
Adds a partial ring with two curved sidewalls tilted at a specific angle to the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane is ZX plane, `addsidewallarc` function will constitute a partial ring structure whose top and bottom are parallel to the ZX plane. 
Used in FDTD and FDE.

**Syntax**
|Code|Function |
|:---|:---|
|`addsidewallarc;`|Adds a partial ring with two slanted and curved sidewalls to the simulation environment according to the current view plane in the composite viewer window.|


**See also**
addarcwaveguide

## addsidewallbezier
**Description**
Adds a curved waveguide with sidewalls curved by specific Bezier to the simulation environment according to the current view plane in the composite viewer window.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addsidewallbezier;`|Adds a curved waveguide with sidewalls curved by specific Bezier to the simulation environment according to the current view plane in the composite viewer window.|


**See also**
addsidewallarc


## addequation
**Description**
Adds a structure determined by specific equation to the simulation environment.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addequation;`|Adds a structure determined by specific equation to the simulation environment.|
|`addequation(x_pos, y_pos, z_pos);`|Adds a structure determined by specific equation with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|

**See also**
addrect

## add2drect
**Description**
Adds a 2D rectangle into the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane in composite window is ZX plane, `add2drect` function will add a 2D rectangle parallel to the ZX plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`add2drect;`|Adds a 2D rectangle into the simulation environment according to the current view plane in the composite viewer window.|
|`add2drect(x_pos, y_pos, z_pos);`|Adds a 2D rectangle with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|

**See also**
addrect


## addvertex
**Description**
Adds a vertex to the selected polygon structure.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addvertex(cord_1, cord_2, order_num);`|Adds a vertex to the selected polygon structure. The first and second input numbers are the first and second coordinates of the new vertex respectively. The new vertex  is specified as *(order_num + 1)* th vertex in all vertices.|
|`addvertex(cord_1, cord_2, order_num, k);`|Adds a vertex to the *k* th selected polygon structure. The first and second input numbers are the first and second coordinates of the new vertex respectively. The new vertex is specified as *(order_num + 1)* th vertex in all vertices. The objects are ordered by their location in the object tree. The uppermost selected object is given the index 1, and the index numbers increase as you go down the tree. |

**See also**
delvertex


## delvertex
**Description**
Deletes the specified vertex of the selected polygon structure.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`delvertex(ver_order_num);`|Deletes the *(ver_order_num + 1)* th vertex of the selected polygon structure.|
|`delvertex(ver_order_num, k);`|Deletes the *(ver_order_num + 1)* th vertex of the *k* th selected polygon structure. The objects are ordered by their location in the object tree. The uppermost selected object is given the index 1, and the index numbers increase as you go down the tree. |

**Example**
Convert a rectangle structure to a triangle structure by deleting its vertex.

```msf
switchtoZXview;
Vertex = [1, 1; 1, -1; -1, -1; -1, 1].*1e-6; # vertices, unit: m
VertexNum = length(Vertex); # number of vertices

# add a polygon structure
addpoly(0, 0, 0);
set('name', 'NewTriangle');
set('vertices', Vertex);

select('NewTriangle');
delvertex(VertexNum - 1); # delete the vertex whose order number is 4
```


**See also**
addvertex


## add2dpolygon
**Description**
Adds a 2D polygon into the simulation environment according to the current view plane in the composite viewer window.
For example, if the current view plane in composite window is ZX plane, `add2dpolygon` function will add a 2D polygon parallel to the ZX plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`add2dpolygon;`|Adds a 2D polygon into the simulation environment according to the current view plane in the composite viewer window.|
|`add2dpolygon(x_pos, y_pos, z_pos);`|Adds a 2D polygon with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|

**See also**
addpoly

## addphotoniccrystal

**Description**
Adds a photonic crystal structure to the simulation environment.
Used in FDTD and FDE.

**Syntax**

|Code|Function|
|:---|:---|
|`addphotoniccrystal;`|Adds a photonic crystal structure to the simulation environment. |
|`addphotoniccrystal(x_pos, y_pos, z_pos);`|Adds a photonic crystal structure with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m). |


**Example**
This example shows how to create a photonic crystal structure with designated properties.

```msf
# switch view plane to ZX plane
switchtoZXview; 

addphotoniccrystal(0, 0, 0);
set('element type', 'ellipse');
set('a', 4e-6); # set lattice constants, unit: m
set('c', 4e-6); 
set('cells x', 4);
set('cells y', 1);
set('cells z', 4);

```

**See also**
addstructuregroup

# Group

## addgroup
**Description**
Adds a group into the simulation environment.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addgroup;`|Adds a group into the simulation environment.|
|`addgroup(x_pos, y_pos, z_pos);`|Adds a group with designated center position(also the origin of the local coordinate system) *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|

**See also**
group, addstructuregroup

## addstructuregroup
**Description**
Adds a structure group into the simulation environment.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addstructuregroup;`|Adds a structure group into the simulation environment.|
|`addstructuregroup(x_pos, y_pos, z_pos);`|Adds a structure group with designated center position(also the origin of the local coordinate system)  *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|

**See also**
group, addgroup

## addanalysisgroup
**Description**
Adds an analysis group into the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addanalysisgroup;`|Adds an analysis group into the simulation environment.|
|`addanalysisgroup(x_pos, y_pos, z_pos);`|Adds an analysis group with designated center position(also the origin of the local coordinate system) *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|

**See also**
group, addgroup

## addtogroup
**Description**
Adds the selected object into designated group or structure group.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addtogroup('group_name');`|Adds the selected object into the group or structure group named *'group_name'* .|


**See also**
addgroup, addstructure

## removefromgroup
**Description**
Removes the selected object from group, structure group or analysis group.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`removefromgroup;`|Removes the selected object from group, structure group or analysis group.|

**Example**
Remove the rectangle name 'Rectangle_1' from group named 'Group'.
```msf
select('Group::Rectangle_1');
removefromgroup;
```

**See also**
addtogroup

## addsetupvariable
**Description**
Adds a new setup variable to the selected structure group or analysis group.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addsetupvariable('value_name', 'value_type', value_data);`|Adds a new setup variable named *'value_name'* to the selected structure group or analysis group. The *'value_type'* can be 'number', 'text', 'length', 'time', 'frequency', 'material', and 'global variable'.|

**Example**
Add a number setup variable named 'new_stvar' to the selected analysis group. 
```msf
select('FDTD::Analysis Group');
addsetupvariable('new_stvar','Number',2.776);
```

**See also**
addgroup, addstructuregroup, addanalysisgroup

## addparametervariable
**Description**
Adds a new parameter variable to the selected analysis group.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addparametervariable('value_name', 'value_type', value_data);`|Adds a new parameter variable named *'value_name'* to the selected analysis group. The *'value_type'* can be 'number', 'text', 'length', 'time', 'frequency', 'material', and 'global variable'.|


**See also**
addsetupvariable, addresultvariable

## addresultvariable
**Description**
Adds a new result variable to the selected analysis group.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addresultvariable('value_name');`|Adds a new result variable named *'value_name'* to the selected analysis group.|

**See also**
addsetupvariable, addresultvariable


# Source

## adddipole
**Description**
Adds a dipole source to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`adddipole;`|Adds a dipole source to the simulation environment.|
|`adddipole(x_pos, y_pos, z_pos);`|Adds a dipole source with center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
addplane, addtfsf, addmodesource, addgaussiansource

## addplane
**Description**
Adds a plane source to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addplane;`|Adds a plane source to the simulation environment.|
|`addplane(x_pos, y_pos, z_pos);`|Adds a plane source with center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
adddipole, addtfsf, addmodesource, addgaussiansource


## addtfsf
**Description**
Adds a tfsf source to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addtfsf;`|Adds a tfsf source to the simulation environment.|
|`addtfsf(x_pos, y_pos, z_pos);`|Adds a tfsf source with center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|



**See also**
adddipole, addplane, addmodesource, addgaussiansource

## addmodesource
**Description**
Adds a mode source to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addmodesource;`|Adds a mode source to the simulation environment.|
|`addmodesource(x_pos, y_pos, z_pos);`|Adds a mode source with center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|



**See also**
adddipole, addplane, addtfsf, addgaussiansource

## addgaussiansource
**Description**
Adds a Gaussian source to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addgaussiansource;`|Adds a Gaussian source to the simulation environment.|
|`addgaussiansource(x_pos, y_pos, z_pos);`|Adds a Gaussian source with center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
adddipole, addplane, addtfsf, addmodesource





## addportgroup
**Description**
Adds a port group to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addportgroup;`|Adds a port group to the simulation environment.|

**See also**
addportgroup




## addmodeport
**Description**
Adds a mode port to the activated port group.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addmodeport;`|Adds a mode port to the activated mode group.|
|`addmodeport(x_pos, y_pos, z_pos);`|Adds a mode port with center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
addportgroup

## addimportsource
**Description**
Adds an import source to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addimportsource;`|Adds an import source to the simulation environment.|
|`addimportsource(x_pos, y_pos, z_pos);`|Adds an import source with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
addportgroup


# Monitor


## addpowermonitor
**Description**
Adds a frequency-domain field and power monitor to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addpowermonitor;`|Adds a frequency-domain field and power monitor to the simulation environment.|
|`addpowermonitor(x_pos, y_pos, z_pos);`|Adds a frequency-domain field and power monitor with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
addfieldmonitor, addtimemonitor, addindexmonitor

## addfieldmonitor
**Description**
Adds a frequency-domain field and power monitor to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addfieldmonitor;`|Adds a frequency-domain field and power monitor to the simulation environment.|
|`addfieldmonitor(x_pos, y_pos, z_pos);`|Adds a frequency-domain field and power monitor with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
addpowermonitor, addtimemonitor, addindexmonitor

 
 
## addtimemonitor
**Description**
Adds a time monitor to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addtimemonitor;`|Adds a time monitor to the simulation environment.|
|`addtimemonitor(x_pos, y_pos, z_pos);`|Adds a time monitor with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
addpowermonitor, addfieldmonitor, addindexmonitor
 
 
 
 
## addindexmonitor
**Description**
Adds an index monitor to the simulation environment.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addindexmonitor;`|Adds an index monitor to the simulation environment.|
|`addindexmonitor(x_pos, y_pos, z_pos);`|Adds an index monitor with designated center position *x_pos*, *y_pos*, *z_pos*(unit: m) to the simulation environment.|


**See also**
addpowermonitor, addfieldmonitor, addtimemonitor 

## addmonitor2dataset
**Description**
Adds the field data *E, H* in the designated monitor to a dataset as the function of position and wavelength.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addmonitor2dataset('monitor_name')`|Returns a dataset containing all field data in the designated monitor. |

**Example**
Add the field data *E, H* in the FDFP monitor named 'FDFP_Monitor' to a dataset.
```msf
EM = addmonitor2dataset('FDTD::FDFP_Monitor')
```

Result:
```
EM =
E ,H vs x, y, z, lambda/f
```




# Material

## addmaterial
**Description**
Adds a new material to the project material library.
Used in FDTD and FDE.

**Syntax**

|Code|Function|
|:---|:------|
|`addmaterial`|Lists all the available material models.|
|`addmaterial('model_name', 'material_name');`|Adds a new material into project material library by the designated name and material model. If added successfully, the function returns 1, otherwise returns 0.|

**Example**
List all material models available. Then, add a dielectric material named 'new_dielc' into the project material library.

```msf
# list all material models available
addmaterial 

# add dielectric material 'new_dielc' 
addmaterial('dielectric', 'new_dielc'); 

```
Result(all material models available):
```msf
val =
dielectric                 
nk                         
conductive                 
sampled data               
drude                      
lorentz                    
debye                      
graphene                   
chi2 nonlinear             
chi3 raman/kerr nonlinear  
pec                        
conductive 2d              
sampled 2d data
```


**See also**
setmaterial, getmaterial

## setmaterial
**Description**
Sets property of the designated material to desired value. 
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`setmaterial`|Lists all the materials in the current material library.|
|`setmaterial('material_name')`|Lists all the property names of specific material that can be modified.|
|`setmaterial('material_name', 'p_name', p_value);`|Sets the property *'p_name'* of the material *'material_name'* to value *p_value*. The argument *p_value* can be a matrix or a string, which must match with the property.|

**Examples**

- List all properties of specific material

  ```msf
  # add new material
  output=addmaterial('graphene', 'new_graphene'); 

  # list all adjustable properties of material 'new_graphene'
  setmaterial('new_graphene') 
  ```
  Result:
  ```msf
  val =
  name                     
  color                    
  tolerance type           
  tolerance                
  max coefficients         
  improve fdtd stability   
  imaginary weight         
  pso user defined         
  pso ratio                
  pso max generations      
  pso generation size      
  scattering rate (eV)     
  chemical potential (eV)  
  temperature (K)          
  conductivity scaling  
  ```
- Use number or string to set property

  Add a graphene material named 'new_graphene' into project material library. Then set the property 'scattering rate (eV) ' to 0.00012 and rename the material.
  ```msf
  output=addmaterial('graphene', 'new_graphene');               # add material

  setmaterial('new_graphene', 'scattering rate (eV)', 0.00012);  # set scattering rate (eV)
  setmaterial('new_graphene', 'name', 'graphene_material');      # rename the material 
  ```

- Use matrix to set property of sampled material

  This example shows how to use matrix to set material property of sampled material.
  To set property 'sampled data' of sampled material, we should create a **sampled data matrix** to store the permittivity data as function of lambda(m). The **sampled data matrix** must have 2 or 4 columns:
  - For isotropic sampled material, the shape of 'sampled data' matrix is n * 2: the first column is lambda(m), the second column is complex permittivity epsr.
  - For anisotropic sampled material, the shape of 'sampled data' matrix is n * 4: the first column is lambda(m), the next three columns are epsr_xx, epsr_yy, epsr_zz.

  ```msf
  lam= linspace(1.5e-6, 0.5e-6, 50);                   # lambda(m) data            
  eps= 3.14+((1i*1e6)/(2*pi*c*eps0)).*lam;           # permittivity data
  sampled_data= [lam; eps].';                         # sampled data matrix 

  output= addmaterial('sampled data', 'sa_cond');     # add sampled  material 
  setmaterial('sa_cond', 'max coefficients', 5);       # set the number of coefficients   
  setmaterial('sa_cond', 'sampled data', sampled_data);# set property  'sampled data' by matrix 
  setmaterial('sa_cond', 'color', [0.1,0.8,0.6]);      # set property 'color' by matrix

  ```

**See also** 
addmaterial, getmaterial

## getmaterial
**Description**
Returns desired property of designated material. 
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:------|
|`getmaterial`|Lists all the materials in the current material library.|
|`getmaterial('material_name')`|Lists all property names of the specific material that can be gained.|
|`mtprop=getmaterial('mt_name', 'p_name');`|Returns the property *'p_name'* of the material *'mt_name'*. The returned variable is either a matrix or a string, depending on the property in the query.|

**Examples**
- List all properties available of a material

  ```msf
  # add new graphene material 
  output=addmaterial('graphene', 'new_graphene');

  # list all property names that can be gained
  getmaterial('new_graphene')  
  ```
  Result:
  ```msf
  val =
  name                     
  color                    
  tolerance type           
  tolerance                
  max coefficients         
  improve fdtd stability   
  imaginary weight         
  pso user defined         
  pso ratio                
  pso max generations      
  pso generation size      
  scattering rate (eV)     
  chemical potential (eV)  
  temperature (K)          
  conductivity scaling
  ```

- This example shows how to get property in the form of string.  
  Add a graphene material named 'new_graphene' and get the value of property 'tolerance type '.
  ```msf
  # add new material
  output=addmaterial('graphene', 'new_graphene');

  # get the value of property 'tolerance type'
  gra_tp=getmaterial('new_graphene', 'tolerance type');
  ```

  Result:
  ```msf
  gra_tp =
          'rmse'  
  ```

- Sampled material: This example shows how to get sampled data (matrix) of a sampled material.

  The returned sampled data (matrix) has 2 or 4 columns:
  - For isotropic sampled materials, the shape of **sampled data matrix** is n * 2: the first column is lambda(m), the second column is complex permittivity epsr.
  - For anisotropic sampled materials, the shape of **sampled data matrix** is n * 4: the first column is lambda(m), the next three columns are epsr_xx, epsr_yy, epsr_zz.

  ```msf
  Ag_sd=getmaterial('Ag (Silver)_CRC', 'sampled data');   # get sampled data 

  ```


**See also** 
addmaterial, setmaterial

## getmaterialmodel
**Description**
Gets index or permittivity data of designated material at specified wavelength (unit: m) .
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`getmaterialmodel('material_name', lambda, d_type);`|Gets index or permittivity data of designated material named *'material_name'* at specified wavelength (unit: m) *lambda* . If d_type is 0, returns the real part and imaginary part of permittivity. If d_type is 1, returns the real part and imaginary part of index.|


>__Note:__
>
>If the input parameter *lambda* is a number or row vector, returns a 2 * N matrix whose first and second row are the real and imaginary part of permittivity(d_type = 0) or index(d_type = 1), respectively. N is the length of *lambda*.
>
>If the input parameter *lambda* is a column vector, returns a N * 2 matrix whose first and second column are the real and imaginary part of permittivity(d_type = 0) or index(d_type = 1), respectively. N is the length of *lambda*.



**Example**
```msf
getmaterialmodel('Ag (Silver)_CRC', 1.24e-6, 1)  # lambda: 1.24 um

```

Result :
```msf
val =
   0.280000206
    9.03000412
```
**See also**
getmaterial


# Common Manipulation

## set
**Description**
Sets the property of the selected object.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`set`|Lists all properties of the selected object that can be modified. |
|`set('property_name', value);`|Sets property named *'property_name'* of the selected object to *value* .|
|`set('property_name', value, k);`|Sets property named *'property_name'* of the *k* th object to *value* when multiple objects are selected. The objects are ordered by their location in the object tree. The uppermost selected object is given the index 1, and the index numbers increase as you go down the tree. |



**Example**

Set property 'x span' of selected object to 5e-6(m).
```msf
set('x span', 5e-6);    # unit: m
```

Set property 'name' of selected object to 'new_rectangle'.
```msf
set('name', 'new_rectangle');
```
Disable 'base on source setting' option of selected object.
```msf
set('base on source setting', 0);
```
Set vertices of selected polygon using matrix.
```msf
addpoly;        # add polygon structure
theta=linspace(0, 2*pi, 6);
theta=theta(1: 5);
x=cos(theta)*1e-6;    # x (unit: m)
y=sin(theta)*1e-6;    # y (unit: m)
V=[x; y];        # vertices 

set('vertices', V);

```

**See also**
setnamed, select, selectall

## setnamed
**Description**
Sets the property of named objects.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|---|---|
|`setnamed('object_name')`|Lists all properties of selected object that can be modified.|
|`setnamed('object_name', 'property_name', value);`|Sets the property *'property_name'* of object *'object_name'* to *value* .|
|`setnamed('group_name::name', 'property_name', value)`|Sets the property *'property_name'* of object *'object_name'* in FDTD or group named *'group_name'* to *value* .|


**Example**

Set property 'x span' of the object named 'new_rectangle' to 5e-6 (m).
```msf
setnamed('new_rectangle', 'x span', 5e-6); # unit: m
```

Disable the 'base on source setting' option of the FDFP Monitor named 'T' in FDTD.
```msf
setnamed('FDTD::T', 'base on source setting', 0);
```

**See also**
set, select

## select
**Description**
Selects the target object. 
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`select('object_name');`|Selects the target object named *'object_name'* .|
|`select('solver_name::object_name');`|Selects the target object named *'object_name'*  in solver named *solver_name* .|
|`select('group_name::object_name');`|Selects the target object named *'object_name'*  in group, structure group or analysis group named *group_name* .|

**Example**
Select the target object named *'Index_Monitor'*  in FDTD solver.
```msf
# add FDTD and index monitor 
addfdtd;

addindexmonitor;
set('name', 'Index_Monitor');

select('FDTD::Index_Monitor');

```


**See also**
selectall

## selectall
**Description**
Selects all the objects in the simulation environment.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`selectall;`|Selects all the objects in the simulation environment.|

**See also**
select

## unselectall
**Description**
Unselects all the objects that have been selected before.
Used in FDTD and FDE.


**Syntax**
|Code	|Function|
|:---|:---|
|`unselectall;`|Unselects all the objects that have been selected before.|

**See also**
select


## pin
**Description**
Pins the selected object.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`pin;`|Pins the selected object.|
|`pin('object_name');`|Pins the object named "object_name".|

**See also**
unpin

## unpin
**Description**
Unpins the selected object.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`unpin;`|Unpins the selected object.|
|`unpin('object_name');`|Unpins the object named "object_name".|

**See also**
pin

## disable
**Description**
Disables the selected object.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`disable;`|Disables the selected object.|
|`disable('object_name')`|Disables the object named 'object_name'.|

**See also**
disable

## enable
**Description**
Enables the selected object.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`enable;`|Enables the selected object.|
|`enable('object_name');`|Enables the object named "object_name".|

**See also**
enable

## copy
**Description**
Copies and pastes the selected object.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`copy;`|Copies and pastes the selected object.|
|`copy('object_name');`|Copies and pastes the object named "object_name".|



# View 

## switchtotopview
**Description**
Switches view plane in the composite viewer window to top view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtotopview;`|Switches view plane in the composite viewer window to top view plane.|

**See also**
switchtobottomview, switchtofrontview, switchtobackview, switchtoleftview, switchtorightview


## switchtobottomview
**Description**
Switches view plane in the composite viewer window to bottom view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtobottomview;`|Switches view plane in the composite viewer window to bottom view plane.|

**See also**
switchtotopview, switchtofrontview, switchtobackview, switchtoleftview, switchtorightview


## switchtofrontview
**Description**
Switches view plane in the composite viewer window to front view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtofrontview;`|Switches view plane in the composite viewer window to front view plane.|

**See also**
switchtotopview, switchtobottomview, switchtobackview, switchtoleftview, switchtorightview

## switchtobackview
**Description**
Switches view plane in the composite viewer window to back view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtobackview;`|Switches view plane in the composite viewer window to back view plane.|

**See also**
switchtotopview, switchtobottomview, switchtofrontview, switchtoleftview, switchtorightview


## switchtoleftview
**Description**
Switches view plane in the composite viewer window to left view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtoleftview;`|Switches view plane in the composite viewer window to left view plane.|

**See also**
switchtotopview, switchtobottomview, switchtofrontview, switchtobackview,  switchtorightview

## switchtorightview
**Description**
Switches view plane in the composite viewer window to right view.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtorightview;`|Switches view plane in the composite viewer window to right view plane.|

**See also**
switchtotopview, switchtobottomview, switchtofrontview, switchtobackview, switchtoleftview

## switchtoZXview
**Description**
Switches view plane in the composite viewer window to ZX view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtoZXview;`|Switches view plane in the composite viewer window to ZX view plane.|

**See also**
switchtoZYview, switchtoXYview

## switchtoZYview
**Description**
Switches view plane in the composite viewer window to ZY view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtoZYview;`|Switches view plane in the composite viewer window to ZY view plane.|

**See also**
switchtoZXview, switchtoXYview

## switchtoXYview
**Description**
Switches view plane in the composite viewer window to XY view plane.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`switchtoXYview;`|Switches view plane in the composite viewer window to XY view plane.|

**See also**
switchtoZXview, switchtoXYview


