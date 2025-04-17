---
title: Basic Operations
description: This section introduces the basic operations including various operations on variables, file operations and data type conversion.
keywords: Basic operation,File operation,Type conversion,System command,Time counting,Change directory(cd),Class,Find
businessId: Script-Commands_basic-operations
language: en-US
sort: 265
published: true
date: 2024-03-04T08:25:09.072Z
tags: 
editor: markdown
dateCreated: 2022-12-27T02:32:51.069Z
---


**This section introduces the basic operations including various operations on variables, file operations and data type conversion.** 


# disp
**Description**
Displays a matrix.
Used in FDTD and FDE.

The `disp` function prints the matrix without the variable label to *Script Console* window.


**Syntax**
|Code|Function|
|:---|:---|
|`disp( S );`|Displays the matrix *S*.|

**See also**
show

# finite
**Description**
Tests variable for finite values.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`out = finite( A );`|`finite` returns a matrix, the same size as the input (A), consisting of ones and zeros. The elements of the return matrix are 1 where the elements of A are finite, or zero where the elements of A are `Inf` or `NaN`.|


**Example**
```msf
a = [1, inf(), 3; 4, 5, 6; inf(), 8, nan()]
b = finite (a)
```
Result:
```msf
a =
             1           inf             3
             4             5             6
           inf             8           nan
b =
             1             0             1
             1             1             1
             0             1             0
```

**See also**
isinf, isnan



# show
**Description**
Shows information about a variable.
Used in FDTD and FDE.


**Syntax**
|Code|Function|
|:---|:---|
|`show( A );`|`show` takes a single argument and returns a brief description of the argument, it's class, name, and any other pertinent characteristics. Note that all the information provided by `show()` can be obtained by other means: `class()`, `type()`, and `size()`. Additionally, direct member reference will provide the same information as `show`.|


**See also**
class, size, type



# what
**Description**
Shows what functions are active in the workspace.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`what($$)`|Shows the names of the functions in the global workspace.|
|`what(STRUCT)`|Shows what functions are in a struct. `what` returns a string matrix of all the names of functions in a struct. If the argument is `$$` (most common usage) then the names of the functions in the global workspace are returned.|      
 
**See also**  
who

# who
**Description**
Shows the variables in a struct.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`who( );`|Returns a string matrix of all the names of the variables currently in the global symbol table.|
|`who($$);`|Returns a string matrix of all the names of the variables currently in the global symbol table.|
|`who( STRUCT );`|Returns the variable names of an RLaB struct.|

**See also** 
what

# whos
**Description**
Prints a description of the variables in a struct.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`whos( S )`|Prints a description of the variables in a struct *S*. The `whos` function prints a tabular listing (to stdout) of the contents of the struct, or symbol-table *S*. Information on functions is not output. If no argument is provided `whos` prints out information from the global-symbol table.|
  

**See also** 
sizeof, who, what

# class
**Description**
Returns a string which identifies the type of the object that A represents. Valid classes are num, string, struct, cell, and function.

Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`out = class( A );`|Identifies the class of *A*.|
|`out = A.class;`|Identifies the class of *A*.|

**Example**

```msf
m = 1;
if(class(m) == 'num') 

   m = m + 1;
end

m
```

Result:

```msf
m =
             2
```

**See also**
show, type


# diary
**Description**
Logs commands (program statements) to a file.
Used in FDTD and FDE.

The `diary` function echoes all input commands and Rlab output to a diary file. If 'file_name' is not specified, then a file named *DIARY* is opened.

The `diary`, used without any arguments, will turn on statement logging, or turn off statement logging if a diary file is already open.

**Syntax**
|Code|Function|
|:---|:---|
|`out = diary( );`|Echoes all input commands and Rlab output to a diary file. If 'file_name' is not specified, then a file named DIARY is opened.|
|`out = diary( 'file_name' );`|Echoes all input commands and Rlab output to the diary file named *'file_name'*.|



# entinfo
**Description**
Returns entity information.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`out = entinfo(VAR);`|Returns the internal address and reference count of *VAR*. |

This function is not intended for general use, so no explanation of the function's purpose, or guarantees regarding its future availability will be made.

**See also**
class


# error
**Description**
Error handling/ reporting.
Used in FDTD and FDE.

The `error` function allows user-functions to jump back to the prompt when some sort of error has occurred. The nature of the error is up to the user. When an error is detected the user simply calls `error()`. If no argument is supplied, `error()` will print the default message. Otherwise, `error` prints the string supplied as an argument, and jumps back to the prompt.

Jumping 'back to the prompt' means execution of the current loop or function is terminated immediately and execution of any prompt-level statements is performed.

**Syntax**
|Code|Function|
|:---|:---|
|`out = error( );`|Prints the default message and allows user-functions to jump back to the prompt.|
|`out = error( 'STRING' );`|Prints the string  *'STRING'* supplied as an argument, and allows user-functions to jump back to the prompt.|




# eval
**Description**
Evaluates expressions.
Used in FDTD and FDE.
The `eval` function evaluates the statement contained in the string argument 'S'. `eval` returns the result of the statement in 'S'. `eval` can be used within functions and can distinguish local and argument variables from global.

Before we go any further, we should note that `eval` is not really a necessary part of RLaB. Users should definitely not use it a crutch as with some other matrix programming languages. The RLaB concept of variables, and the struct class are more efficient ways of dealing with function evaluations and variable names than `eval`.

**Syntax**
|Code|Function|
|:---|:---|
|`out = eval( 'S' );`|Evaluates expressions *'S'*.|

**Example**
```msf
eval('printf("Hello!")');
```
Result:

```msf
Hello!
```

# exist
**Description**
Checks the existence of a variable.
Used in FDTD and FDE.

The `exist` function returns TRUE (1) if VAR exists, and FALSE (0), if VAR does not exist. VAR is any valid variable name.

If you need to know if a variable exists, and if it is a function or data, then use the `exist` function in conjunction with the class or type functions.

**Syntax**
|Code|Function|
|:---|:---|
|`out = exist( 'var_name' );`|Checks the existence of a variable named 'var_name'.|



**Example**
```msf
a = 3;
        

exist('a')
            
```
Result:
```msf
val =
             1

```

**See also**
class, type, who, what

# find
**Description**
Finds non-zeros.
Used in FDTD and FDE.
`find` returns a matrix that contains the indices of the non-zero elements of the input matrix A.

**Syntax**
|Code|Function|
|:---|:---|
|`out = find(A);`|Returns a matrix that contains the indices of the non-zero elements of the input matrix *A*.|

**Example**

A common usage for `find`, is the selection of matrix elements that meet certain criteria.
```msf
 a = rand(4,4)
 x = a[ find( a < .1 )]
```
Result:
```msf
a =
   0.460981667  0.0106171295   0.290495008   0.268887907
   0.519936681   0.414229393   0.205473974   0.334269047
   0.160773635   0.232932165   0.561298728   0.277925879
   0.974579871   0.555183232   0.791246772   0.788529098
x =
  0.0106171295
```


# findstr
**Description**
Finds the designated sub-string in the input string and returns corresponding information.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`findstr('sub_str', 'total_str');`|Finds the designated sub-string in the input string and returns a vector containing the order numbers of the first letters of sub-strings that meet the requirement.|


**Example**

```msf
total_str = 'This is a string.'

findstr('string', total_str)
```

Result:

```msf
total_str =
This is a string.  
val =
            11
```
**See also**
find



# findnearest
**Description**
Finds the element that nearest the input data.
Used in FDTD and FDE.
`findnearest` returns a vector that contains the index of the element that is nearest to the input data, and the difference *Delta_data* between the data and the elements.

**Syntax**
|Code|Function|
|:---|:---|
|`[Ind, Delta_data] = findnearest(data, point);`|Returns a vector *Ind* that contains the index of the element that is nearest to the input data *data*, and the difference *Delta_data* between the data and the elements.|


**Example**
```msf
a = [-1, 4, 1.5, 0.2, -0.2]
[ind, delta] = findnearest(a,0.5)

```
Result:
```msf
a =
            -1             4           1.5           0.2          -0.2
ind =
             4

delta =
          -1.5           3.5             1          -0.3          -0.7

```
# almostequal
**Description**
Executes an almost-equal comparison.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`[logic_num, delta_data] = almostequal(data, standard_data, re_delta);`|Returns 1 when \|data - standard_data\|  is less than or equal to \|data + standard_data\|/2 * re_delta, otherwise returns 0. The relative difference *re_delta* is defaulted to 1e-15. |
|`[logic_num, delta_data] = almostequal(data, standard_data, re_delta, abs_delta);`|Returns 1 when \|data - standard_data\| <= \|data + standard_data\| /2 * re_delta or \|data - standard_data\| <= abs_delta, otherwise returns 0. The relative difference *re_delta* and absolute difference *abs_delta* are all defaulted to 1e-15.|
|`[logic_num, delta_data] = almostequal(data, standard_data, re_delta, abs_delta, number);`|Executes an almost-equal comparison according to the mode designated by input *number*. The absolute difference *abs_delta* is defaulted to 1e-15. The meanings of the input parameters can be seen as follows.|

The meanings of the input parameters can be seen as follows:

|input parameter|meaning|default|
|:---|:---|:---|
|data|the data to be compared with standard data |--|
|standard_data|standard data used to compare with input data |--|
|re_delta|relative difference, returns 1 when \|data - standard_data\| is less than or equal to \| data + standard_data \| /2 \* re_delta, otherwise returns 0. |1e-15|
|abs_delta|absolute difference, returns 1 when \| data - standard_data\| is less than or equal to abs_delta, otherwise returns 0. |1e-15|
|number|comparation mode control, when number==0, re_delta is valid. |0(fewer than four inputs) or 2(four inputs)|


*Note:*
When number is 0, re_delta is valid(default); 
When number is 1, re_delta and abs_delta are valid, and the logical relationship is \&\& ; 
When number is 2, re_delta and abs_delta are valid, and the logical relationship is \|\|;
When number is 3, abs_delta is valid.



**Example**
```msf
# |0.9 - 1.1| < (1.1 + 0.9 ) *0.5 * 0.6 
almostequal(0.9, 1.1, 0.6)

# |0.9 - 1.1 | > (1.1 + 0.9) * 0.5 * 0.1
almostequal(0.9, 1.1, 0.1)

```
Result:
```msf
val =
             1
val =
             0
```


# getenv
**Description**
Searches the current environment for a variable with name NAME. 
Used in FDTD and FDE.


**Syntax**
|Code|Function|
|:---|:---|
|`out = getenv ( NAME )`|Gets an environment variable. The value of the environment variable is returned as a string.|

*Note:*
Exactly how `getenv` behaves depends upon the underlying operating system implementation. On UNIX system `getenv` will return a `NULL` string if the environment variable does not exist.


**See also**
putenv

# isempty
**Description**
Tests a matrix or struct for elements:

   Returns 1 if A is empty.
   Returns 0 if the matrix has any elements.

Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`isempty(A)`|Tests a matrix or list for elements.|



# isreal
**Description**
Tests if a matrix is ALL real.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`out = isreal ( A )`|`isreal` tests its argument, A, and returns TRUE (1) if A's elements are all real, or FALSE (0) if any of A's elements are complex. 
|


**See also**
any

# isinf
**Description**
Tests for values of infinity.
Used in FDTD and FDE.


**Syntax**
|Code|Function|
|:---|:---|
|`out = isinf ( A )`|`isinf` returns TRUE (1) if A is Infinity (according to IEEE-754). If A is a vector or a matrix the test is performed element-by-element, and a matrix the same size as A is returned. `Infs` can usually be created by attempting to divide by zero, or using the builtin `inf` function.|



**Example**

```msf
a = [1, 2, 3; 4, 5, inf(); 7, 8, 9]
a_isinf = isinf(a)

```
Result:
```msf
a =
             1             2             3
             4             5           inf
             7             8             9
a_isinf =
             0             0             0
             0             0             1
             0             0             0
```

**See also**
isnan, finite

# isnan
**Description**
Tests for NaN values.
Used in FDTD and FDE.


**Syntax**
|Code|Function|
|:---|:---|
|`ut = isnan ( A )`|`isnan` returns TRUE (1) if A is a `NaN` (Not A Number). If A is a vector or a matrix the test is performed element by element, and a matrix the same size as A is returned. `NaNs` can be created by the 0/0 operation on most computers.|


**Example**
```msf
a = [1, 2, 3; 4, 5, nan(); 7, 8, 9]
a_isnan = isnan(a)
```
Result:
```msf 
a =
             1             2             3
             4             5           nan
             7             8             9
a_isnan =
             0             0             0
             0             0             1
             0             0             0
```

**See also**
inf, isinf, finite, nan

# issymm
**Description**
Tests matrix for symmetry.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`out = issymm ( A )`|`issymm` returns TRUE (1) if the argument A is a symmetric (or Hermitian) matrix, and FALSE (0) if A is not symmetric (Hermitian).|


# isfield
**Description**
Examines the struct to see if it includes the specified field. 
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`tf=isfield(S,field_name)`| Examines struct *S* to see if it includes the field specified by *field_name*. Output *tf* is set to logical 1 (true) if *S* contains the field, or logical 0 (false) if not. If *S* is not a struct, `isfield` returns false.|

**Example**
 
``` msf
s=struct(a=2,b=3)
            
isfield(s,'a')  # returns 1 when contains the element
            
isfield(s,'a2') # returns 0 when not contains
            
isfield(2,'a')  # return 0 when first argument is not a struct
      
```

Result:

```msf
s =
  struct with fields:
    a: 2
    b: 3
val =
             1
val =
             0
val =
             0
```

# rmfield
**Description**
Removes the specific fields from struct.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`rmfield(s,field)`|  Removes the specified field or fields from structure array s. Specify multiple fields using a cell array of character vectors or a string array. |

**Example**
Remove the defined fields.
```msf
s=struct(a=3,b=5,c=5,d=6)
          
s=rmfield(s,['a','b']) # This can also be written as "s=rmfield(s,{'a','b'})" .
           
s    
```
Result:

```msf
s =
  struct with fields:
    a: 3
    b: 5
    c: 5
    d: 6
s =
  struct with fields:
    c: 5
    d: 6
s =
  struct with fields:
    c: 5
    d: 6

```


# members
**Description**
The `members` function takes a variable as an argument (L), and returns a string-vector containing the object's member names.
Used in FDTD and FDE.

For example: 
`x = members ($$)`  will create a row-vector and assign it to x. The row-vector will contain the names of all the elements in the global-symbol-table.

The `members` function is probably most useful when used in conjunction with for-loops. The result of `members` can be used as the loop index, allowing users to operate on the elements of an object. 

**Syntax**
|Code| Function|
|:---|:---|
|`out = members ( L )`|Returns an object's member names.|

**Example**
```msf
a = rand(2, 3)

members( a )
```

Result:

```msf
a =
   0.399200201  -0.277332842 -0.0150899477
   -1.76820695   0.611103237   0.456874043
val =
nr  nc  n  class  type  storage  
```
**See also**
type

# type
**Description**
Returns the type of an object.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`out = type ( A )`|Returns a string that describes the type of elements contained in object A. The valid types for an object vary according to the class of the object. For example, the valid types of a matrix are *real, complex* , and *string* which are determined by the elements it contains. If the input object is a struct having a field named *type* , then the `type` function will report the contents of that member.|
|`A.type`|The type of elements contained in object can also be determined by using the type member reference. |

**Example**
```msf
mat_real = [1, 2, 3];
mat_complex = [1+2i, 3+4i];
st = struct('x': 0, 'type': 'This is the type information.');

mat_real.type

mat_complex.type

st.type

```

Result:
```msf
val =
real  
val =
complex  
val =
This is the type information.   
```

**See also**
class, show

# tic
**Description**
Starts the timer.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`tic( )`|Internally marks the time at which it was invoked. To measure elapsed time, use `tic` in conjunction with `toc`.|



**Example**

```msf
tic();
a = rand(100,100);
eig(a);
toc()
```

The above would measure the time spent generating the 100x100 random matrix, and calculating the eigenvectors and eigenvalues.

**See also**
toc

# toc
**Description**
Measures time elapsed since `tic`.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`toc( )`|Reports the time (in seconds) elapsed since the last call to `tic`.|


**See also**
tic



# tmpnam
**Description**
Generates temporary file name.
Used in FDTD and FDE.



**Syntax**
|Code| Function|
|:---|:---|
|`out = tmpnam( )`|Returns a string that is not the name of an existing file. `tmpnam` generates a different name each time it is called. The string `tmpnam` returns can be used as a filename for RLaB's file I/O functions. |


**See also**
fopen, fclose, read, write, fprintf



# system
**Description**
Executes operating system commands. 
Used in FDTD and FDE.


**Syntax**
|Code| Function|
|:---|:---|
|`out = system( COMMAND )`|The `system` function behaves like the the UNIX system call. The string argument to `system`, COMMAND, is passed directly to the operating system command-line shell for execution. The program waits until the system call is finished.|


**Example**
On Linux operating system, the following code will allow the user to edit (create) the file test.r. When the vi process is finished the user will be back at the RLaB prompt.
```msf
system( 'vi test.r' )
```

The following code will then load the result of the vi process.
```msf
rfile test
```

On Windows operating system, the following code can be used to start the notepad program.

```
system('notepad')
```


# putenv
**Description**
Changes or adds an environment variable.
Used in FDTD and FDE.

`putenv` takes a single string argument of the form:

`'NAME=VALUE'`
        
`putenv` makes the value of the environment variable NAME equal to VALUE by altering an existing variable or creating a new one.

Exactly how `putenv` behaves depends upon the underlying operating system implementation.

On most Unix systems `putenv` will return non-zero if an error occurred, and zero otherwise.


**Syntax**
|Code| Function|
|:---|:---|
|`out = putenv ( 'NAME=VALUE' )`|Changes or adds an environment variable.|



**See also**
getenv

# fseek
**Description**
Reposition a stream.
Used in FDTD and FDE.


**Syntax**
|Code| Function|
|:---|:---|
|`out = fseek ('file_name', offset )`|Sets the current position in file named 'file_name', a subsequent read will access data beginning at the new position. The new position is the location shifted by the specified number of characters relative to the beginning of file. The *offset* is the number of characters used to shift.|
|`out = fseek('file_name', offset, origin)`|Sets the current position in file named 'file_name', a subsequent read will access data beginning at the new position. The new position is the location shifted by the specified number of characters relative to the position *origin*. The *offset* is the number of characters used to shift.|

The *origin* can be:
- 'SEEK_SET' beginning of file (default)
- 'SEEK_CUR' current position
- 'SEEK_END' end of file


**See also**
fread, open, close


# getline
**Description**
Gets a line of input.
Used in FDTD and FDE.

`getline` returns an N-element struct which contains all of the tokens from a line in the file described by FN. The tokens are delimited by whitespace. Numbers are installed in the struct as numeric scalars, everything else is installed as scalar strings.

The struct elements have numeric indices, and are numbered from 1 to N. The 1st element containing the 1st token on the line, and the Nth element containing the last token on the line. The newline is not returned as a token.

`getline` will also recognize everything enclosed within a pair of ' as a string, including escape characters.
`getline` will always return a struct-object. When an empty-line has been read, `getline` returns a struct with only one field whose value is an empty string. `getline` will terminate on an End-Of-File (EOF).

The second, and optional argument, LL, forces `getline` to return the entire line (including the newline) as a string, without any parsing. If LL is <= 0, then `getline` will read lines as long as 512 characters. If LL > 0, then `getline` will read lines as long as LL characters. The return value is a single string, not a struct, when LL is used. If getline encounters an EOF, while LL is being used, a numeric value of 0 is returned.

**Syntax**
|Code|Function|
|:---|:---|
|`out = getline(FN)`|Returns an N-element struct which contains all of the tokens from a line in the file described by *FN* .|
|`out = getline(FN, LL);`|Returns the entire line (including the newline) as a string. If LL is <= 0, then `getline` will read lines as long as 512 characters. If LL > 0, then `getline` will read lines as long as LL characters. |


**Example**
Given a file named *test*, which contains the following lines:
```msf
jcool  259  4 1075  822 vt01     S   Dec 29  9:32 X :0 -p 1 -s 5 
jcool  256  0   21    0 console  S   Dec 29  0:00 startx 
jcool  261  0  338   88 console  S   Dec 29  0:16 twm 
jcool  288  8  635  333 ?        S   Dec 29  2:00 emacs 
jcool  287  0  408   65 console  S   Dec 29  0:01 xclock 
```
Run the following code,
```msf
tmp = getline( 'test' );
```
would produce a struct variable named *tmp* with 16 elements: tmp.[1] would be the string 'jcool' and tmp.[16] would be the number 5. The next call to `getline()` would read the second line in the file, and create a new struct containing those elements.

To read the entire contents of a file:
```msf
ans = getline('file_name');
if (length (ans)) 

  # do something with ans
else
  # finish up
end
```
Since `getline` returns an empty struct when there is no input, we can tell when to terminate the input loop by checking the length of the returned struct.

Using the optional second argument to `getline` we can get old-style Fortran formatted output. For example, we have a file filled with:
```msf
0.1285186E+000.1463163E+000.0000000E+000.0000000E+000.0000000E+000.0000000E+00
0.0000000E+000.0000000E+000.0000000E+000.0000000E+000.7322469E-010.5245288E-01
0.0000000E+00-.9399651E-010.2397120E-01-.6551484E-010.2616772E+020.5796479E-01
0.0000000E+000.2500000E+000.7788281E-010.2121489E-010.0000000E+00-.1345507E+00
0.1516225E-01-.1284981E+000.1136876E+020.3010250E-010.0000000E+00-.2500000E+00
```
we can do:
```msf
lv = strtod (getline (FN, 14));
```
and get a vector with the numeric values for each line by using the results.

**See also**
strsplt


# setstr
**Description**
Translates a vector of integers to a string of ASCII characters.
Used in FDTD and FDE.
`setsrt` converts a vector of integers in n to a string of ASCII characters. Only integer values between 0 and 127 will be converted successfully. Nonprintable characters will be translated to their symbols surrounded by braces.


This is useful when `fread` is used to read "char" type data from a file. `fread` returns an integer vector.

```msf
name=fread(file_name,8,"char");
sname=setstr(name);
```

The example lines above will read in 8 bytes of characters into integer vector name. Then name is converted to a string sname by `setstr`.

This file is a substitute for the same in matlab by Derrick Early.
       
**Syntax**
|Code|Function|
|:---|:---|      
|`S = setstr( n );`|Translates vector *n* of integers to a string of ASCII characters.|   



# strsplt
**Description**
Splits a string.
Used in FDTD and FDE.
`strsplt` returns a row matrix that contains a single character string as each element. The resulting matrix has as many columns as the input argument had characters.

**Syntax**
|Code|Function|
|:---|:---|
|`out = strsplt( STR );`|Returns a row matrix that contains a single character string as each element.|
|`out = strsplt( STR, FW );`|Returns a row matrix that contains a single character string as each element. The second, and optional, argument to `strsplt`, FW forces `strsplt` to split STR into FW length strings. FW can also be a string, or a string matrix, specifying the field separators that `strsplt` will use. |


**Example**
```msf
smat = strsplt( 'string' )
show(smat)
```

Result:
```msf
smat =
s  t  r  i  n  g  
	nr                  :	1
	nc                  :	6
	n                   :	6
	class               :	string
	type                :	string
	storage             :	dense
```
The second, and optional, argument to `strsplt`, FW forces `strsplt` to split STR into FW length strings. FW can also be a string, or a string matrix, specifying the field separators that `strsplt` will use:
```msf
str = 'this;is;a;sem-colon;separated string;with numbers;1.234'

strsplt(str,';')
```

Result: 

```msf
str =
this;is;a;sem-colon;separated string;with numbers;1.234  
val =
this  is  a  sem-colon  separated string  with numbers  1.234        
```

**See also**
getline

# strtod
**Description**
String to decimal conversion.
Used in FDTD and FDE.
The `strtod` function converts its argument 'STR' from string class to numeric class. `strtod` stands for 'string to decimal'.

`strtod` will return a `NaN` (Not a Number) if it cannot recognize a string, or an element of a string matrix, as a number.
**Syntax**
|Code|Function|
|:---|:---|
|`out = strtod( 'STR' );`|The `strtod` function converts its argument 'STR' from string class to numeric class.|


# strtol
**Description**
String to integer conversion.
Used in FDTD and FDE.

The `strtol` functions converts its argument 'STR' from string class to numeric class. `strtol` stands for 'string to long-int'. The second (optional) argument BASE, specifies the conversion base. Valid values for BASE are between 2 and 32. BASE defaults to 10 if not specified.
`strtol` will return a `NaN` (Not a Number) if it cannot recognize a string, or an element of a string matrix, as a number.

**Syntax**
|Code|Function|
|:---|:---|
|`out = strtol( 'STR' , BASE )`|Converts argument 'STR' from string class to numeric class.|

# cd
**Description**
Changes the current program folder. 
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`cd('new_folder');`|Changes the current program folder to the designated folder named *'new_folder'*.|

**See also**
changeworkpath

# changeworkpath
**Description**
Changes the current work path to the designated path.
Used in FDTD and FDE.

**Synatx**
|Code|Function|
|:---|:---|
|`changeworkpath('new_work_path');`|Changes the current work path to the designated path.|

**See also**
getworkpath
         
# the end of a statement
**Description**
A statement can end with ';' or empty. The return value will be printed when it ends with empty, and the return value will not be printed when it ends with *';'*.
Used in FDTD and FDE.

**Syntax**
|Code |Function|
|:---|:---|
|`statement`|The return value will be printed when ends with empty.|
|`statement;`|The return value will not be printed when ends with ';'.|


**Example**
```msf
b = 2

c = 3;
```

Result:
```msf
b =
             2

```
      
         