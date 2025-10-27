---
title: Data Input and Output 
description: This section describes the functions about the data initialization, import and export such as clear, clc, savematlabmatfile, and loadmatlabmatfile.
keywords: Data input,Data output,Initialization,Clear,Delete,Save matlab matfile,Save project,Load matlab matfile,Read data
businessId: Script-Commands_data-input-and-output
language: en-US
sort: 263
published: true
date: 2024-02-07T07:06:57.219Z
tags: basic syntax, initialization_save_load
editor: markdown
dateCreated: 2022-12-13T07:23:18.418Z
---


**This section describes the functions about the data initialization, import and export.**

# Initialization

## clear
**Description**
Clears all or specified stored workspace variables.
Used in FDTD and FDE.
 
**Syntax**
|Code| Function |
|:---|:---|
|`clear;`| Clears all workspace variables and returns the number of variables cleared successfully. |
|`clear('var_name_1', 'var_name_2', ...);`|Clears the designated variables named *'var_name_1'*, *'var_name_2'*, ... in workspace. Then returns the number of variables cleared successfully. |
 
**Example**
```msf
b = 1;
c = 2;
 
clear( 'b' );
```
## clearall
**Description**
Clears all workspace variables.
Used in FDTD and FDE.

**Syntax**
|Code|	Function |
|:---|:---|
|`clearall;`|Clears all workspace variables and returns the number of variables cleared successfully.|
 
**See also**
clear


## clc
**Description**
Clears script console.
Used in FDTD and FDE. 
 
**Syntax**
|Code| Function |
|:---|:---|
|`clc;`|Clears all input and output from the script console. |
 
**See also**
clear

## delete
**Description**
Deletes the selected objects.
Used in FDTD and FDE.

**Syntax**
|Code| Function |
|:---|:---|
|`delete;`| Deletes the selected objects.|
|`delete('object_name');`| Deletes the object named *'object_name'*.|
 
**Example**

Delete the index monitor named "new_index_monitor" of FDTD Solver.

```msf
delete('FDTD::new_index_monitor');
```
 
**See also**
clear


## deleteall
**Description**
Deletes all the objects.
Used in FDTD and FDE. 
 
**Syntax**
|Code| Function |
|:---|:---|
|`deleteall;`| Deletes all the objects.|
 
**See also**
delete

## clearglobalvariable 
**Description**
Clears the designated global variable. 
Used in FDTD and FDE.
 
**Syntax**
|Code|	Function|
|:---|:---|
|`clearglobalvariable('variablename');`| Clears the global variable named *'variablename'*.|
 
**See also**
clearallglobalvariable

## clearallglobalvariable
**Description**
Clears all the global variables. 
Used in FDTD and FDE.

**Syntax**
|Code|	Function|
|:---|:---|
|`clearallglobalvariable;`|Clears all the global variables.|

**See also**
clearglobalvariable



# Export

## savedatafile
**Description**
Saves data to .mdf(MaxCloud Data File) file.
Used in FDTD and FDE.
 
**Syntax**
|Code| Function|
|:---|:---|
|`savedatafile('file_path');`|Saves all the current variables in the *Script Workspace* to the specified .mdf file. If the 'file_path' is not an absolute path, the current path is the work path.|
|`savedatafile('file_path', var1, var2, ...);`| Saves the specified variables in the *Script Workspace* to the designated .mdf file. If the 'file_path' is not an absolute path, the current path is the work path.|
 
**Example**  
```msf
b=[1,2];
jh=[3,4;5,7];
savedatafile('data', b, jh);
```
The .mdf file *data.mdf* will be saved in the work path.
 
**See also**
savematlabmatfile


## savematlabmatfile
**Description**
Saves data to .mat (MATLAB-FILE) file.
Used in FDTD and FDE.
 
**Syntax**
|Code| Function |
|:---|:---|
|`savematlabmatfile('file_path');`|Saves all current variables to the specified .mat file. If the 'file_path' is not an absolute path, the current path is the work path.|
|`savematlabmatfile('file_path', var1, var2...)`| Saves the specified variables to the .mat file. If the 'file_path' is not an absolute path, the current path is the work path.|
 
**Example**
```msf
b=[1,2];
jh=[3,4;5,7];
savematlabmatfile('data',b,jh);
```
 
The .mat file *data.mat* will be saved in the work path.
 
**See also**
loadmatlabmatfile


## saveproject
**Description**
Saves the project file according to the file path.
Used in FDTD and FDE.
 
**Syntax**
|Code | Function |
|:---|:---|
|`saveproject;`|Saves current project.|
|`saveproject('file_path');`|Saves the project file to the location specified by *'file_path'*.|
 
**Example**
```msf
saveproject('F:\projects\new_project.mpps');
```
 
**See also**
loadproject

## saveh5file

**Description**

Saves data to h5df file.

Used in FDTD and FDE.

**Syntax**

|Code|Function|
|:---|:---|
|`saveh5file( file_path, var_1, var_2, ..., var_N )`| Saves the specified variables *var_1* , *var_2* , ... , *var_N* to the h5df file. |


**Example**

Saves variables to h5df file.

```msf
file_path = 'D:\H5\example.h5';

a = 1; 
b = 'str';

# save variables a and b to the h5df file named example.h5
saveh5file( file_path, a, b );
```


**See also**

loadh5file



## saveascii
**Description**
Saves data to .mdfascii (MaxCloud Data File by Ascii) file.
Used in FDTD and FDE.
 
**Syntax**
|Code| Function |
|:---|:---|
|`saveascii('file_path');`|Saves all current variables to the specified .mdfascii file. If it is not an absolute path, the current path is the work path.|
|`saveascii('file_path', var1, var2, ... );`|Saves the specified variables to the .mdfascii file.|
 
**Example**  
```msf
b=[1,2];
jh=[3,4;5,7];
saveascii('data',b,jh);
```
The .mdfascii file data.mdfascii will be saved in the work path.
 
**See also**
loadascii
 
## fprintf
**Description**
Formatted printing to a file.
Used in FDTD and FDE.

**Syntax**
|Code| Function |
|:---|:---|
|`out = fprintf ( file_num, format_string, var_1, var_2, ... )`|Formatted printing to a file.|


- file_num
The 1st argument determines the file to which the output is sent. The *file_num* can be generated by `fopen` function.


- format_string
A valid `fprintf` format string such as `"%d"`.

- var_1, var_2, ...
The *var_1*, *var_2*, ... are any number of constants or variables that match the format string. `fprintf` cannot print out vector, matrix, cell, struct objects as a whole. Valid print objects are strings, constants, and scalars.

**Example**

```msf
# write the string "str" into file "stdout.txt"

# open the file before writing
f = fopen("stdout.txt", "w+"); 

fprintf(f, "%s, %s", "Hello", "world!");

```

**See also**
printf, sprintf, write, read


## fwrite
**Description**
Binary stream output. 
Used in FDTD and FDE.


**Syntax**
|Code| Function |
|:---|:---|
|`out = fwrite ( 'file_name', type, data )`| `fwrite` writes *data* to the file identified by *'file_name'*. The *data* is cast, or converted to the data type identified in *type*. `fwrite` roughly mimics the C programming language's `fwrite` library function. The *data* can either be a dense numeric matrix, or a string matrix. The size of the matrix does not need to be specified because the entire matrix is written. If *data* is a string matrix, then the first character of each element is written to the file named *file_name*, after being coerced to type *type*. Allowable type arguments are num and string. |


**See also**
fread, fseek, close, open, write


## format
**Description**
Sets the printing format.
Used in FDTD and FDE.

`format` sets the output print format for all numeric output. If no arguments are supplied, then the output print formats are reset to the default values.

**Syntax**
|Code| Function |
|:---|:---|
|`out = format( )`|Sets the output print format for all numeric output. If no arguments are supplied, then the output print formats are reset to the default values.|
|`out = format( PRECISION )`|Sets the output print format for all numeric output with  designated precision.|
|`out = format( WIDTH, PRECISION )`|Sets the output print format for all numeric output with  designated minimum field width and  precision.|

The meanings of the input parameters are as follows:

- PRECISION
Represents the precision with which numbers will be printed. For instance, if PRECISION has a value of 4, then 4 significant digits will be printed for numeric values.

- WIDTH
Represents the minimum field width of the formatted output.

`format` returns a 2-element matrix containing the previous width and precision values. Subsequently, this matrix can be used to reset format.


**Example**
Example 1:

```msf
123456789.123456789
format(10);
123456789.123456789
```
Result:
```msf
val =
   123456789
val =
 123456789.1


```

Example 2:

```msf
format();
a = rand(3,3) 
format(10);
a
format(15,10);
a

```
Result:

```msf 
a =
       0.57      0.831      0.462
      0.683     0.0735      0.435
      0.396      0.464       0.63
a =
   0.5701993108   0.8312915564   0.4622091651
   0.6828844547  0.07354432344   0.4351293147
   0.3963157833   0.4644346535   0.6302834153
a =
     0.5701993108     0.8312915564     0.4622091651
     0.6828844547    0.07354432344     0.4351293147
     0.3963157833     0.4644346535     0.6302834153
```


## printf
**Description**
This `printf` function is a limited implementation of the C-language `printf()`, and does not support all C-language data types.
Used in FDTD and FDE.

**Syntax**
|Code| Function |
|:---|:---|
|`out = printf ( formatstring , VARi ... )`|Formatted printing.|

The meanings of the input parameters are as follows:
- formatstring
This parameter must be a valid `printf` format string.
- VARi
VARi are any number of constants or variables that match the format string. `printf` cannot print out vector, matrix, or struct objects as a whole. Valid print objects are strings, constants, and scalars.

**Example**

The following shows how one might print out the annotated contents of a matrix.
```msf
a = rand(2,3);
a_size = size(a);

for(i = 1 : a_size(1))
 
  for(j = 1 : a_size(2))
  
    printf("a[%i;%i] = %f\n", i, j, a[i,j]);
  end
end
```
Result:
```msf
a[1;1] = 0.110975
a[1;2] = 0.773031
a[1;3] = 0.131552
a[2;1] = 0.699178
a[2;2] = 0.956544
a[2;3] = 0.228156

```     
However, it would be more efficient to use:
```msf
print(a);
```

**See also**
fprintf, sprintf, write, read


## write 
**Description**
Writes a string to the file and adds a newline.
Used in FDTD and FDE.

**Syntax**
|Code| Function |
|:---|:---|
|`write(filename, input_word)`|Writes *input_word* into file named *filename*.|

**See also**
writem


   

## writem
**Description**
Writes the matrix data to the file in designated format.
Used in FDTD and FDE.


`writem` is the counterpart to `readm`. `writem` writes the matrix data to the file denoted by the 1st argument in a generic format.

The format used is:
```
line 1:     value[1;1]     ...  value[1;ncol] \n
...
line nrow:  value[nrow;1]  ...  value[nrow;ncol] \n
```   

`writem` will write real and complex numeric matrices, as well as string matrices even though `readm` can only read real numeric matrices. Complex matrices are written as a single 2*nrow by ncolumn real matrix. Sparse matrices are written as triplets (row column value) for each element of the matrix.

`writem` does not close the file after writing A. The file is left open for further writes if necessary. `fclose` can be called to explicitly close the file.

**Syntax**
|Code| Function |
|:---|:---|
|`out = writem ( 'filename' , A )`|Writes a matrix in ASCII format.|

**Example**
```msf
a = [1, 2, 3];
writem("stdout.txt", a)
fclose("stdout.txt")
```

**See also**
fclose, getline, open, readm, write


## writeascii
**Description**
Writes object(s) to file in ASCII format.
Used in FDTD and FDE.

The `writeascii` function takes at least two arguments. The 1st argument is the string that identifies the file to write to. The file is opened with write permission, destroying any pre-existing contents. The file is left open so that subsequent writes will append to the file, and not destroy the contents.

The arguments after the file name are the objects that will be written. 

**Syntax**
|Code| Function |
|:---|:---|
|`out = writeascii( FILENAME , A , b , ... )`|Writes object(s) to file in ASCII format.|


**Example**
```msf
writeascii( 'filename', a , b , c );
```
The above code will open the file named filename in write mode, and write the contents of the variables a, b, and c.

**See also** 
close, read, readascii

## spwrite
**Description**
Writes sparse matrix to the designated file.
Used in FDTD and FDE.


The `spwrite` function takes at least two arguments. The 1st argument is the string that identifies the file to write to. The file is opened with write permission, destroying any pre-existing contents. The file closed after the matrix is written.

The default format for the sparse matrix is the internal storage format: compressed row-wise storage.

A third, and optional argument, is a string specifying either the default, or an optional output format. The value of the string can be either 'sparse' (default) or 'graph'. The graph output is a file suitable for use with the Metis or Chaco graph partitioning/re-ordering software.


**Syntax**
|Code| Function |
|:---|:---|
|`out = spwrite( FILENAME, SPM, FORMAT )`|Writes the sparse matrix *SPM* to the file named *FILENAME* according to the designated format *FORMAT*.|


**See also**
write

## sprintf
**Description**
Formatted printing to a string.
Used in FDTD and FDE.

This `sprintf` function is a limited implementation of the C-language `sprintf()`, and does not support all C-language data types.

**Syntax**
|Code| Function |
|:---|:---|
|`out = sprintf( stringvar, formatstr, VARi ... )`|Formatted printing to a string.|

The meanings of the input parameters are as follows: 
- stringvar
The output of `sprintf` is written to this variable.
- formatstr
A valid `sprintf` format string.
- VARi
Are any number of constants or variables that match the format string. `sprintf` cannot print out vector, matrix, or struct objects as a whole. Valid print objects are strings, constants, and scalars.

**See also**
printf, fprintf, write, read



 
# Import

## loaddatafile
**Description**
Loads MaxCloud Data (.mdf data) into workspace.
Used in FDTD and FDE. 
 
**Syntax**
|Code| Function |
|:---|:---|
|`loaddatafile('file_path');`|Loads the data of the specified .mdf file to the workspace.|
|`loaddatafile('file_path', var);`| Loads the data in the specified .mdf file into defined variable *var* . If *var* is a struct variable, it will be attached to *var* , otherwise *var* will be assigned as a struct variable.|
 
**Example**  
```msf
# The data in data.mdf will be loaded into workspace.
loaddatafile('data.mdf');
 
var = struct();
# The data in data.mdf will be packaged into a struct variable and assigned to var.
loaddatafile('data.mdf',var);
```
 
## loadmatlabmatfile
**Description**
Loads the data in the designated .mat file into workspace.
Used in FDTD and FDE.
 
**Syntax**
|Code| Function |
|:---|:---|
|`loadmatlabmatfile('file_path');`|Loads all the data in designated .mat file  into workspace. |
|`loadmatlabmatfile('file_path', var);`|Loads the data in designated .mat  file  into variable *var* . If *var* is a struct variable, it will be attached to *var*, otherwise *var* will be assigned as a struct variable.|
 
**Example**  
```msf
# The data in data.mat will be loaded into workspace.
loadmatlabmatfile('data.mat');
 
# The data in data.mat will be packaged into a struct variable and assigned to var.
var = struct();
loadmatlabmatfile('data.mat', var);
 
```

## loadproject
**Description**
Loads a project file according to the file path.
Used in FDTD and FDE.
 
**Syntax**
|Code | Function |
|:---|:---|
|`loadproject('file_path');`|Loads a project file according to the *'file_path'*.|
 
**Example**
```msf
loadproject('F:\projects\new_project.mpps');
```
 
**See also**
saveproject

## loadh5file

**Description**

Imports the specific h5df file.

Used in FDTD and FDE.

**Syntax**

|Code|Function|
|:---|:---|
|`loadh5file( file_path ) `| Imports the data in the h5df file specified by file path *file_path* . The input *file_path* must be a string or a string variable. |
|`loadh5file( file_path, var )`| Stores the data in h5df file specified by *file_path* to the struct *var* . If *var* is a struct variable, it will be attached to *var*, otherwise *var* will be assigned as a struct variable. |

**Example**

Import data in h5df file.

```msf
file_path = 'D:\H5\example.h5';

loadh5file( file_path );

```

**See also**

saveh5file


## loadascii
**Description**
Loads data in specified .mdfascii file into workspace.
Used in FDTD and FDE.
 
**Syntax**
|Code|Function|
|:---|:---|
|`loadascii('file_path');`|Loads data in specified .mdfascii file into workspace. |
|`loadascii('file_path', var);`| Loads data in specified .mdfascii file into defined variable *var*. If *var* is a struct variable, it will be attached to *var*, otherwise *var* will be assigned as a struct variable. |
 
**Example**  
```msf
# The data in data.mdfascii will be loaded into workspace.
loadascii('data.mdfascii');
 
# The data in data.mdfascii will be packaged into a struct variable and assigned to var.
var = struct();
loadascii('data.mdfascii',var);
```
**See also**
saveascii

## fopen
**Description**
Opens the designated file.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`file_id = fopen('file_path');`|Opens the file according to the designated path. The output *file_id* is the number used to identify the opened file.|
|`file_id = fopen('file_path', 'access_type');`|Opens the file according to the designated access type. The output *file_id* is the number used to identify the opened file.|

The `fopen` functions allows user to specify the file access mode. The allowed file access modes are as follows:

|Access type string|Description|
|:---|:---|
|'r'|Opens a file for reading. The file to be opened must exist.|
|'w'|Opens an existing file or creates a new file for writing. The existing contents will be covered.|
|'a'|Opens an existing file or creates a new file for appending. The new contents will be written after the existing contents.|
|'r+'|Opens a file for reading and writing and the file must exist. The existing contents will be covered.|
|'w+'|Opens an existing file or creates a new file for reading and writing. The existing contents will be covered.|
|'a+'|Opens an existing file or creates a new file for reading and appending. The new contents will be written after the existing contents.|


**See also**
fclose

## fclose
**Description**
Closes the designated file.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`fclose('file_path');`|Closes the designated file.|


**See also**
fread




## fread
**Description**
Reads specified number of data in the designated type from the designated file and returns the result in a numeric matrix.
Used in FDTD and FDE.


**Syntax**
|Code|Function|
|:---|:---|
|`out = fread( FILENAME, NITEMS, TYPE, SWAPB )`|Reads specified number (NITEMS) of data in the designated type TYPE from file named FILENAME (a string) and returns the result in a numeric matrix.|



The meanings of the input parameters are as follows:
- NITEMS
Number of objects of type TYPE to read from file named FILENAME. If NITEMS is inf(), then `fread` will read from the file named FILENAME until end-of-file is reached.

- TYPE
'char'
'unsigned char'
'short int'
'unsigned int'
'int'
'float'
'double'
- SWAPB
0 Do not swap bytes in a word (default).
1 Do swap the bytes in each word.


**See also**
fseek, fwrite, close, open, write



## readm 
**Description**
Reads ASCII matrix from a file.
Used in FDTD and FDE.


`readm` reads a generic matrix of data from the file denoted by the string argument FILENAME. The return value is the newly created matrix. The second, and optional, argument is a two-element matrix that specifies the size of the matrix to read.

If the matrix size is not specified, then the matrix is filled row-wise with the input data. Otherwise (if the size is specified), the matrix is filled column-wise, as the input is read.

The file format is generic ASCII. The rows of the matrix are separated by newlines, and the columns are separated by whitespace. Unnecessary newlines, either before, or after the data will confuse `readm`, and will probably result in an error message. Only one matrix can be stored in a file. If you need to store more than one matrix in a file, use `write`, and `read`.

`readm` can only read in numeric matrices. The result of reading in string matrices is undefined.


**Syntax**
|Code|Function|
|:---|:---|
|`readm(FILENAME)`|Reads ASCII matrix from the file named FILENAME. The matrix is filled row-wise as the input data is read.|
|`readm( FILENAME, [NR, NC] )`|Reads ASCII matrix from the file named FILENAME. The matrix whose size is specified by vector [NR, NC] is filled column-wise when reading data.|

**Example**

```msf
1 2 3 4
5 6 7 8
9 10 11 12
```

The above values in a file called 'test' would be read in like:

```msf
 > a = readm('test')
 a =
 matrix columns 1 thru 4
        1          2          3          4  
        5          6          7          8  
        9         10         11         12 
```

`readm` exists to read in data from other programs. In many cases a simple awk script will filter the other programs output into one or more columns of data. `readm` will read the data into the matrix, then the matrix can be reshaped if necessary.

Notes:
`readm` has no idea how many rows are in the matrix it is reading. This is because `readm` can work with pipes and process output where it gets the matrix as a stream. `readm` uses a heuristic to guess how many rows of the matrix to allocate at one time. A second, optional argument, [NR, NC] can be specified if the heuristic does not yield the performance you desire. The heuristic is purposely memory conservative.

 `readm ( 'filename' , [NR, NC] )`

**See also**
reshape, getline, open, read, writem

## rfile
**Description**
Loads an rfile.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`rfile`|Prints a list of all the files with a '.r' suffix.|
|`rfile name`|Loads an rfile named *name*.|


`rfile name` loads the contents of the file denoted by `name` into the workspace. The `name` argument is NOT a string, and does not have to include the '.r' suffix.

Allowable names for rfiles are filenames that start with a digit or a letter (a-z or A-Z) and contain digits, letters, hyphens(-), and underscores(_).
You may not be able to use all the possible filenames allowed by the host operating system.

If the relevant environment variable is not set, a pre-defined default search path will be used. This path is typically set to the current working directory ('.').
`rfile` is a command, not an expression or statement. Therefore, it must be issued on a line by itself, and cannot occur in the midst of another statement or expression. The `rfile` command cannot be continued across lines (no continuations).
The command `rfile name` can be used more than once. Each time the command is issued the file *name.r* is loaded.
The `rfile` command tries to be friendly. If you give it a string without the '.r' extension, it will automatically add one for you. If you give it a string with the '.r' extension, it will leave it alone.
The file may contain any valid commands or function definitions. There is no limit to the number of functions defined in a file, and both commands and function definitions can be included in the same file.

**Example**
```msf
rfile roots.r poly bode 
```
**See also**
load
 
 
## readascii
**Description**
`readascii` reads the file identified by the FILENAME. The file is opened with read access, and all of the contents are read. The entities in the file are installed in the global symbol table, overwriting any existing entities. Upon completion the file is closed.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`out = readascii( FILENAME )`|Reads ASCII data from a file named *FILENAME*.|
|`out = readascii( FILENAME, X )`|Reads ASCII data from a file named *FILENAME* into struct variable *X*.|



**Example**
Reads ASCII data from the file named *bunch_of_data_in_a_file*.
```msf
readascii ('bunch_of_data_in_a_file');    
```

The second form of the function allows the data in the file to be read into struct variable X. The global-symbol-table is untouched (except for X).

```msf
 readascii ('bunch_of_data', X); 
```       
The contents of the file bunch_of_data are read and stored in the struct variable X. Except for the creation/modification of the variable X, the global-symbol-table is unchanged.

**See also**
close, getline, read, readm, writem, writeascii

## readb
**Description**
Reads designated file in binary mode.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`readb('file_path');`|Reads designated file in binary mode.|

**See also**
readascii


## readgraph
**Description**
Reads graph data from designated file.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`readgraph('file_path');`|Reads data of the unweighted graph from the designated file. The returned matrix A is a sparse matrix which can be seen as the adjacent matrix of the graph. The correct format of the file read by readgraph function is explained below.|

The correct format of the file read by `readgraph` function is as follows:
```
num_vertices(number of vertices) num_edge(number of edges)
adjacent vertex indexes of the first vertex:   a11 a12 … 
adjacent vertex indexes of the second vertex:  a21 a22 …
…
```

The following is a correct instance:
```
3 2
2 3
1
1
```

**See also**
readb



