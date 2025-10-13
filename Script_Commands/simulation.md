---
title: Simulation
description: This section introduces the functions that can be used to control simulation.
keywords: Simulation control,Job management,Add Finite Difference Time Domain(FDTD) solver,Add Finite Difference Eigenmode(FDE) solver,Run job
businessId: Script-Commands_simulation
language: en-US
sort: 23
published: true
date: 2024-02-18T02:34:20.936Z
tags: simulationcontrol
editor: markdown
dateCreated: 2022-06-14T08:40:58.420Z
---


**This section introduces the functions that can be used to control simulation.**

# Add Solver

## addfdtd
**Description**
Adds a FDTD solver into the current simulation project.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`addfdtd;`|Adds a FDTD solver into the current simulation project.|
|`addfdtd(x_pos, y_pos, z_pos);`|Adds a FDTD solver into the current simulation project. The *x_pos*, *y_pos*, *z_pos*(unit: m) are the center position of the FDTD simualtion region.|


**See also**
addfde, addfdfd

## addfde
**Description**
Adds a FDE solver into the current simulation project.
Used in FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addfde;`|Adds a FDE solver into the current simulation project.|
|`addfde(x_pos, y_pos, z_pos);`|Adds a FDE solver into the current simulation project. The *x_pos*, *y_pos*, *z_pos*(unit: m) are the center position of the FDE simulation region.|


**See also**
addfdtd, addfdfd


## addfdfd
**Description**
Adds a FDFD solver into the current simulation project.
Used in FDFD.

**Syntax**
|Code|Function|
|:---|:---|
|`addfdfd;`|Adds a FDFD solver into the current simulation project.|
|`addfdfd(x_pos, y_pos, z_pos);`|Adds a FDFD solver into the current simulation project. The *x_pos*, *y_pos*, *z_pos*(unit: m) are the center position of the FDFD simulation region.|



**See also**
addfdtd, addfde


## addmesh
**Description**
Adds a mesh into the current simulation project.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addmesh;`|Adds a mesh into the current simulation project.|
|`addmesh(x_pos, y_pos, z_pos);`|Adds a mesh into the current simulation project. The *x_pos*, *y_pos*, *z_pos*(unit: m) are the center position of the mesh.|


**See also**
addfdtd, addfde, addfdfd

# Simulation Control

## run
**Description**
Runs the current simulation.
Used in FDTD and FDFD.

**Syntax**
|Code|Function|
|:---|:---|
|`run;`|Runs the current simulation.|

**Example**
Suppose in FDTD simulation environment, run the current project and get its simulation status.

```msf
run;
getdata('FDTD','simulation status')  #returns 0/1/2/3/4/5, and the meanings are as follows.
# 0: the project has not been run before
# 1: finished all simulation time
# 2: manual stop
# 3: early shutoff
# 4: divergence
# 5: abnormal exit
```

**See also**
simulation, runjobs, runanlysis

## solvemode
**Description**
Solves modes using the selected mode source, port, FDE solver or FDFP monitor whose mode expansion option has been enabled.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`solvemode;`|Solves modes using the selected mode source, port, FDE solver or FDFP monitor whose mode expansion option has been enabled. |
|`solvemode('object_name');`|Solves modes using the mode source, port, or FDFP monitor named *'object_name'*. |
|`solvemode('parent_name::object_name');`|Solves modes using the mode source, port, FDFP monitor named *'object_name'* in group, analysis group, port group or solver named *parent_name*. |

**Example**
Solve modes using mode source named *'Mode Source'* in FDTD.
```msf
solvemode('FDTD::Mode Source');

```
**See also**
run

## runsetup
**Description**
Runs the setup script in the structure group or analysis group.
This function can force setup script to be executed immediately.  
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`runsetup;`|Runs the setup script in the structure group or analysis group.|


**See also**
runanalysis


## runanalysis
**Description**
Runs the analysis script in the analysis group.
Used in FDTD.

**Syntax**
|Code|Function|
|:---|:---|
|`runanalysis;`|Runs the  analysis scripts in all analysis groups.|
|`runanalysis('analysis_group');`|Runs the analysis script in the analysis group named *'analysis_group'* . |

**Example**
Runs the analysis script in the analysis group  named 'Analysis_Group_Test_1' in FDTD.
```msf
runanalysis('FDTD::Analysis_Group_Test_1');

```
**See also**
run

## getresourceinfo
**Description**
Gets the basic resource information of CPU and GPU.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`getresourceinfo` |Lists all the basic information of CPU and GPU.|


**Example**

List all the basic information of CPU and GPU.
```msf
getresourceinfo
```
Result:
```msf
val =
CPU:
    CPU id: 0
        name: CPU
        cores: 16
        memory: 31.9278 GB

NVIDIA GPU:
    GPU id: 0
        name: NVIDIA GeForce GTX TITAN X
        graphic memory: 11.9999 GB
        major: 5
        tcc: 0
```

**See also**
get


# Job Management

## clearjobs
**Description**
Clears simulation files in the job manager.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`clearjobs;`|Clears all simulation files in the job manager.|
|`clearjobs('solver_type');`|Clears  simulation files of designated solver in the job manager.|

**Example**
Clears  simulation files of FDE solver in the job manager.

```msf
clearjobs('fde');
```

**See also**
addjobs

## listjobs
**Description**
Lists simulation files in the job manager queue.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`L = listjobs;`|Lists all simulation files in the job manager queue.|
|`L = listjobs('solver_type');`|Lists all simulation files of designated solver in the job manager queue.|

**Example**

```msf
L = listjobs('fdtd');

L

```
Result :
```msf
L =
fdtd:                      
F:/fdtd_project_test.mpps
```

**See also**
clearjobs, addjob



## addjob
**Description**
Adds simulation file to the job manager queue.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`addjob('file_path', 'solver_type');`|Adds simulation file specified by *'file_path'* to the job manager queue.|

**Example**
Adds simulation file to job manager.
```msf
addjob('D:\test_file.mpps', 'FDTD');

```

**See also**
runjobs


## runjobs
**Description**
Runs simulation files in the current job manager queue.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`runjobs;`|Runs the jobs of the activated solver in current simulation project. If there is no activated solver, runs the jobs of FDTD solver.|
|`runjobs('solver_type');`|Runs simulation files of designated solver in the job manager queue.  |
|`runjobs('solver_type', parallel_set)`|Runs simulation files of designated solver in  the job manager queue . If *parallel_set* is 0, runs jobs in single process mode. If *parallel_set* is 1, runs jobs using  parallel settings specified in the job manager.|


**See also**
addjobs


