---
title: Getting Data
description: This section introduces the functions that can be used to get properties and result data from objects.
keywords: Get simulation result,Access property,Get electric data,Get magnetic data,Get sweep result,Get optimization result
businessId: Script-Commands_getting-data
language: en-US
sort: 21
published: true
date: 2024-02-06T02:50:33.584Z
tags: datagetting
editor: markdown
dateCreated: 2022-06-14T08:40:10.224Z
---

**This section introduces the functions that can be used to get properties and result data from objects.**

# Accessing data
## get
**Description**
Gets the specific property value from selected object. 
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`get`|Lists all the properties that can be gained from the selected object.|
|`get('property_name');`|Gets the value of the property named *'property_name'* from the selected object. |
|`get('porperty_name', k);`|Gets the value of the property named *'property_name'*  from the *k* th selected object when multiple objects are selected. The objects are ordered by their location in object tree. The uppermost selected object is given the index 1, and the index numbers increase as you go down the tree. |


**Example**

Add a new rectangle structure and rename it. Then select it and list all its properties that can be gained.
```msf
addrect;                       # add a rectangle structure
set('name', 'new_rectangle');  # rename

select('new_rectangle');
get                            # list all the properties that can be gained 
```

Result:
```msf
val =
first rotation                 
first rotation axis            
index                          
material                       
mesh order                     
name                           
opacity                        
override default transparency  
override mesh order            
second rotation                
second rotation axis           
third rotation                 
third rotation axis            
use relative coordinate        
x                              
x max                          
x min                          
x pos                          
x span                         
y                              
y max                          
y min                          
y pos                          
y span                         
z                              
z max                          
z min                          
z pos                          
z span

```

Get x pos (m) of new_rectangle:
```msf
select('new_rectangle');
x_pos = get('x pos');        # get x pos (m) of new_rectangle
```

Result:
```msf
x_pos=
        0
```


**See also**
select, addrect, set


## getnamed
**Description**
Gets the specific property value from named object.
Used in FDTD and FDE.

**Syntax**
|Code|	Function|
|:---|:---|
|`getnamed('obj_name')`|Lists all the properties that can be gained from the object named *'obj_name'* . |
|`getnamed('obj_name', 'prop_name');`|Gets the value of property *'prop_name'* from the object named *'obj_name'* . |

**Example**
Example 1:

Add a rectangle in current simulation project and list all the names of properties that can be gained from it.

```msf
addrect;
set('name', 'new_rectangle');

getnamed('new_rectangle')

```

Result :
```msf
val =
first rotation                 
first rotation axis            
index                          
material                       
mesh order                     
name                           
opacity                        
override default transparency  
override mesh order            
second rotation                
second rotation axis           
third rotation                 
third rotation axis            
use relative coordinate        
x                              
x max                          
x min                          
x pos                          
x span                         
y                              
y max                          
y min                          
y pos                          
y span                         
z                              
z max                          
z min                          
z pos                          
z span             
```

Example 2:
```msf
addrect;
set('name', 'new_rectangle');

getnamed('new_rectangle', 'x')    # get x pos (m) of new_rectangle
```

Result :
```msf
val =
             0
```

**See also**
get



## getunits
**Description**
Gets scale of the designated physical quantity to SI.
Used in FDTD and FDE.

**Syntax**
|Code|	Function|
|:---|:---|
|`getunits('physical_quantity');`|Gets the scale of the designated physical quantity to SI. The *'physical_quantity'* can be  *‘length'* , *'time'* , or *'frequency'* . |

**Example**

```msf
length_scale = getunits('length')

```

Result(the value of length_scale):
```msf
length_scale =
         1e-06
```


**See also**
get

## getnumber
**Description**
Returns the number of selected objects in object tree.
Used in FDTD and FDE.

**Syntax**
|Code|	Function|
|:---|:---|
|`getnumber`|Returns the number of selected objects in object tree.|

**Example**

Add three objects and select them.
```msf
addpoly;
addrect;
addcircle;

selectall; # select three objects

getnumber

```

Result :
```msf
val =
             3

```

**See also**
select



## getworkpath
**Description**
Gets the current work path.
Used in FDTD and FDE.

**Syntax**
|Code|	Function|
|:---|:---|
|`getworkpath`|Gets the current work path.|

**See also**
getprogrampath

## getprogrampath
**Description**
Gets the current program path.
Used in FDTD and FDE.

**Syntax**
|Code|	Function|
|:---|:---|
|`getprogrampath`|Gets the current program path.|

**See also**
getworkpath


## havedata
**Description**
Queries if the selected object(including solver, source, monitor, and analysis group) has the desired data.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`havedata`|List all the datasets that the selected object has.|
|`havedata('object_name', 'data_name');`| Return 1 if the object named *'object_name'* has the data named 'data_name'.|

**Example**
Select the FDFP monitor in FDTD, then run the following code.

```msf
havedata()
```

Result:
```msf
val =
E (vector: Ex, Ey, Ez )  
H (vector: Hx, Hy, Hz )  
P (vector: Px, Py, Pz )  
power                  
T
```
**See also**
havesweepoptdata


## getdata
**Description**
Gets data from the selected object.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`getdata`|Lists all the data that can be gained from the selected object.|
`getdata('object_name', 'data_name'); `|Gets the data named *'data_name'* from the object called *'object_name'* . |
|`getdata(ID,'data_name');`|Gets the data named *'data_name'* from the object whose ID is *ID* . |
|`getdata('object_name', 'dtset_name', 'data_name');`|Gets the data named *'data_name'* in the dataset called *'dtset_name'* of the object called *'object_name'* . |
|`getdata(ID,'dtset_name', 'data_name');`|Gets the data named *'data_name'* in the dataset called *'dtset_name'* of the object whose ID is *ID* . |

**Example**
Get index_x data in the index dataset from the index monitor named 'Index Monitor' in FDTD.
```msf
getdata('FDTD::Index Monitor', 'index', 'index_x');
```

**See also**
get, select, dataset

## getrawdata
**Description**
Gets raw data from the designated object.
Used in FDTD and FDE.

**Syntax**
|Code	|Function|
|:---|:---|
|`getrawdata`|Lists all the raw data that can be gained from the selected object.|
|`getrawdata('obj_name', 'data_name');`|Gets raw data *'data_name'* from the designated object named *'obj_name'* .|

**Example**
```msf
select('FDTD::FDFP Monitor');
getrawdata

```

Result:
```msf
val =
dx
dy
dz
f
lambda
simulation_dimension
simulation_type
spatial_type
x
y
z  
```
**See also**
getdata

## getdataset
**Description**
Gets result from sources, monitors, or analysis-groups in the form of dataset.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`getdataset('object_name', 'dataset_name')` |Gets the result named 'dataset_name' from the sources, monitors, or analysis-groups named 'object_name' in the form of dataset.|

**Example**
Gets the electric field dataset from the FDFP Monitor named 'new_FPFP' of the Analysis Group in FDTD.

```msf
E_dtset = getdataset('FDTD::Analysis Group::new_FDFP', 'E');
```

**See also**
getdata


## getsolverdata
**Description**
Gets data in current solvers.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`getsolverdata('solver_results');`|Gets data in current solvers.|


**Example**
Get the data named 'dimension' from the 3D FDTD solver.  
```msf
dim=getsolverdata('dimension')

dim
```
Result:
```msf
dim =
             3
```
**See also**
getdata


## getelectric
**Description**
Gets square of the electric field amplitude from the designated monitor.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`getelectric('monitor_name');`|Gets square of the electric field amplitude from the monitor named *'monitor_name'* .|

**Example**
Gets square of the electric field amplitude from the FDFP monitor named 'Global Field' in FDTD.

```msf
E_mag = getelectric('FDTD::Global Field');
```

**See also**
getmagnetic


## getmagnetic
**Description**
Gets square of the magnetic field amplitude from the designated monitor.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`getmagnetic('monitor_name');`|Gets square of the magnetic field amplitude from the monitor named *'monitor_name'* .|

**Example**
Gets square of the magnetic field amplitude from the FDFP monitor named 'Global Field' in FDTD.

```msf
H_mag = getmagnetic('FDTD::Global Field');
```

**See also**
getelectric

## getdipolepower
**Description**
Gets dipole power from the designated dipole source.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`getdipolepower(lambda);`|Gets dipole power at the specified wavelength *lambda* (unit: m) from all the dipole sources.|
|`getdipolepower(lambda, 'dipole_source_name');`|Gets dipole power at the specified wavelength *lambda* (unit: m) from the designated dipole source.|

**See also**
getsourcepower



## getsourcepower
**Description**
Gets source power from the designated source.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`getsourcepower(lambda);`| Gets the source power used to normalize transmission calculations at the wavelength (unit: m) points designated by the vector *lambda* from all sources. |
|`getsourcepower(lambda, 'source_name') `|Gets the source power from the source named 'source_name' used to normalize transmission calculations at the wavelength (unit: m) points designated by the vector *lambda* .|

**Example** 
Get source power from the selected dipole source.

```msf
p = getsourcepower([1.55e-6; 1.2e-6], 'FDTD::Dipole Source');

```
**See also**
getsourceintensity, getsourcenorm

## getsourceintensity
**Description**
Gets source intensity from the selected source.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`getsourceintensity(lambda);`|Gets source intensity at the wavelength (unit: m) points designated by the vector *lambda* from all sources.| 
|`getsourceintensity(lambda, 'source_name'); `|Gets source intensity from the source named 'source_name' at the wavelength (unit: m ) points designated by the vector *lambda* .|

**Example**
Get source intensity from the selected plane source.

```msf
I = getsourceintensity([1.55e-6; 1.2e-6], 'FDTD::Plane Source');
```

**See also**
getsourcepower, getsourcenorm


## getsourcenorm
**Description**
Gets normalized spectrum from the selected source.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`getsourcenorm(lambda); `|Gets normalization spectrum at the wavelength (unit: m) points designated by the vector *lambda*. |
|`getsourcenorm(lambda, 'source_name');`|Gets normalization spectrum at the wavelength (unit: m) points designated by the vector *lambda* , using the source named 'source_name'. |

**Example**
Gets normalized spectrum using the plane source named 'Plane Source' in FDTD.

```msf
lambda = linspace(1.55, 1.65, 50);
source_norm = getsourcenorm(lambda.*1e-6, 'FDTD::Plane Source');

```
**See also**
getsourcepower, getsourceintensity


## getsourcelist

**Description**

Gets the information of sources in current simulation project.

Used in FDTD.

**Syntax**

|Code|Function|
|:---|:---|
|`ids = getsourcelist( 'id' );`|Returns a 1 * N matrix named *ids* containing all the ids of sources in current simulation project. N is the number of sources. |
|`names = getsourcelist( 'name' );`|Returns a 1 * N matrix named *names* containing all the names of sources in current simulation project. N is the number of sources. |
|`sourceInfo = getsourcelist();`|Returns a 1 * N cell named *sourceInfo* consisting of structs. For each source, its information(id, name, visibility) will be stored in an independent struct as the element of the cell *sourceInfo* . N is the number of sources. For a specific source, if it is enabled, its visibility will be 1, otherwise its visibility will be 0. |



**Example**

Example 1:

Gets all the information of sources in current simulation project.

```msf
sourceInfo = getsourcelist();

# display name, id, and visibility of specific source
printf( "source_name:%s\n", sourceInfo{1}.name );
printf( "source_id:%d\n", sourceInfo{1}.id );
printf( "source_visibility:%d\n", sourceInfo{1}.visibility );
```

Result: 
```msf
source_name:Plane
source_id:3
source_visibility:1
```

Example 2:

Gets all the id numbers of sources in current simulation project.

```msf
ids = getsourcelist( 'id' );

ids 
```

Result:
```msf 
ids =
             8             3             2

```

**See also**

getsourcepower, getsourceintensity, getsourcenorm

## selectparent
**Description**
Selects the parent object of current object.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`selectparent; `|Selects the parent object of current object. |

**See also**
getparentdata

## getparentdata
**Description**
Gets data in parent object.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`getparentdata('data_name'); `|Gets the data named *'data_name'* in parent object. The function can only be used in analysis group or analysis data which has parent object. |

**See also**
selectparent


## ishomogeneity
**Description**
Checks out whether the refractive index of the material is same as the index from index monitor.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`ret = ishomogeneity(myname,index0,epsilon);`|Checks out whether the refractive index of the material *index0* is same as the index from the index monitor named *myname*. If each element of *abs(real(index - index0))* is smaller than *0.5\* epsilon*,  returns 1, otherwise returns 0. |
|`ret = ishomogeneity(myname,index0);`|Checks out whether the refractive index of the material *index0* is same as the index from the index monitor named *myname*. In this case, the *epsilon* is 2.2205e-16 .|
|`ret = ishomogeneity(myname);`|Checks out whether the refractive index of the material *index0* is same as the index from the index monitor named *myname*. In this case, the *index0* and *epsilon* are 1 and 2.2205e-16 respectively.|


**See also**
getdata


# Accessing data in sweep 
## havesweepoptdata
**Description**
Queries if the selected parameter sweep, optimization sweep, or S-Matrix sweep has the desired data.
Used in FDTD.

**Syntax**
|Code	|Function|
|:---|:---|
|`havesweepoptdata('sweep_name', 'data_name');`| Return 1 if the parameter sweep, optimization sweep, or S-Matrix sweep that named 'sweep_name' has the data named *'data_name'* .|

**See also**
havedata


## getsweepoptdata

**Description**
Gets result from the parameter sweep, optimization or s-matrix sweep.
Used in FDTD.

**Syntax**
|Code	|Function
|:---|:---|
|`getsweepoptdata('sweep_name', 'dataset_name') `|Gets the dataset named *'dataset_name'*  from the parameter sweep, optimization, or s-matrix named *'sweep_name'* . |
|`getsweepoptdata('sweep_name', 'dataset_name', 'data_name') `|Gets the data named *'data_name'* in the dataset named *'dataset_name'* of the designated parameter sweep, optimization, or s-matrix sweep. |


**Example**
Get the data 'fom history' in the dataset 'fom history' from the optimization called 'new optimization'.
```msf
fom_history = getsweepoptdata('new_optimization', 'fom history', 'fom history');
```

**See also**
getdata, sweep
