---
title: Script Variables
description: This section introduces various powerful data types and corresponding operations provided for users to process different kinds of data. Furthermore, some commonly-used mathematical and physical constants and special characters are predefined for convenient usage.
keywords: Matrix,String,Struct,Cell,Dataset,Script variables,Data type,Pi,Operation rule,Light speed,Physical constant,Mathematical constant,Special character,Predefined character
businessId: Script-Commands_script-variables
language: en-US
sort: 261
published: true
date: 2024-02-18T01:32:34.206Z
tags: data_types_and_operation_rules, basic syntax
editor: markdown
dateCreated: 2024-01-05T08:20:59.367Z
---


**This section introduces the basic data types and operation rules. We provides various powerful data types and corresponding operations for users to process different kinds of data. Furthermore, some commonly-used mathematical and physical constants and special characters are predefined for convenient usage.**

# variable

## number
**Description**
The data type to store integer, floating point format or complex number type data.
Used in FDTD and FDE.

**Syntax**

|Code|Function|
|:---|:---|
|`a = num;`|Creates an integer or floating point number type varaible named *a*, and its value is *num*.|
|`z = real_part + imag_parti;`|Creates a complex number type varaible named *z*, whose real part is *real_part* and imaginary part is *imag_part*.|
|`z = real_part + imag_partj;`|Creates a complex number type varaible named *z*, whose real part is *real_part* and imaginary part is *imag_part*.|

The name of the number type variable can  consist of numbers, letters and underscore characters(_). But the keywords of the script library like `if`, `else`, `elseif`, `while`, `for`, `break`, `continue`, `return`, `function`, `end`, `rfile`, `local`, `global`, `static`, `struct`, `try`, `catch` can not be used.

**Operation**
There are many operations that can be used on number type data.
When using these operations to, the precedence levels is important. Precedence levels determine the order in which RLAB evaluates an expression. Within each precedence level, operators have equal precedence and are evaluated from left to right. The precedence rules for RLAB operators are shown in this list, ordered from highest precedence level to lowest precedence level:
|Priority| Description(Character) |
|:---|:---|
|1(highest)| parentheses `( )` |
|2|logical negation ( `~` ) |
|3|complex conjugate ( `'` ) , transpose ( `.'` ) |
|4|matrix power ( `^` ), power ( `.^` )|
|5|unary plus ( `+` ), unary minus ( `-` ) |
|6|multiplication ( `.*` ), right division ( `./` ), left division ( `.\` ), matrix multiplication ( `*` ), matrix right division ( `/` ), matrix left division ( `\` ) |
|7|addition ( `+` ), subtraction ( `-` ) |
|8|less than ( `<` ), less than or equal to ( `<=` ), greater than ( `>` ), greater than or equal to ( `>=` ) |
|9|equal to ( `==` ) ,  not equal to ( `~=` ) |
|10| logical AND ( `&&` ) |
|11| logical OR ( `\|\|` ) |
|12(lowest)| colon operator ( `:` ) |



**Example**
Example 1 :
Create a complex number.
```msf
z = 3.2 + 2j ;  # create a complex number
```

Result:
```msf
z =
      3.2 +           2i
```

Example 2 :
The default precedence can be overridden using parentheses.

```msf
a = 2;
b = a + 1 .* 2;
d = (a + 1) .* 2;
```
Result :

```msf
b =
             4
             
d =
             6
```


## matrix
**Description**
Matrix type data creation, operation, and example.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`m = [a11, a12,... ; a21, a22,...];`|Creates a matrix with designated data. The *,* symbol means the separation of different columns, while the *;* means the separation of different rows. |
|`m = [m_1, m_2];`|Creates the new matrix by conbining the columns of the existing matrix. |
|`m = [m_1; m_2];`|Creates the new matrix by conbining the rows of the existing matrix.|

**Operation**
Matrix Arithmetic Operations :

|Operation|Description|
|:---|:---|
|`A + B` | element-by-element addition | 
|`A - B` | element-by-element subtraction |
|`A * B` | matrix multiplication |
|`A .* B`| element-by-element matrix multiplication | 
|`A / B` | right-division |
|`A ./ B`| element-by-element right-division |
|`A \ B` | left-division(solve `Ax = B`) |
|`A .\ B`| element-by-element left-division |

Matrix Operations(get or assign elements of matrix) :

|Operation|Description|
|:---|:---|
|`A(:)`    | Forces a matrix into a column vector. |
|`A(:, n)` | Gets or assigns elements of a column from matrix. |
|`A(m, :)` | Gets or assigns elements of a row from matrix. |
|`A(: , m , :) = []`| Deletes the selected dimension. When using this, the index can have only one non-full index like `A(:, 1, :) = []` , while the code `A(:, 1, 2) = []` is not allowed. |


**Example**
Example 1:
Use the existing matrix to create a new matrix.
```msf
a = [1, 2]; 
b = [3; 4]; 
c = [ [a; a], [b, b] ]
```
Result:
```msf  
c =
             1             2             3             3
             1             2             4             4
```

Example 2: 
Create different dimension matrix.
```msf
# 1-dimensional row vector
vector_row = [1, 2, 3, 4];
# 1-dimensional column vector
vector_col = [1; 2; 3; 4];  
# 3*3 matrix
matrix = [1, 2, 3, 4; 1, 2, 3, 4; 1, 2, 3, 4; 1, 2, 3, 4];  
# 4-dimensional matrix
E = zeros(50,40,30,5);
```

Example 3:
Get and delete designated elements of matrix:

```msf
A = [1, 2 ; 3, 4 ; 5, 6]

a = A(2 , :) # get elements in the second row
A(2, :) = [] # delete the second row
 
```
Result:
```msf
A =
             1             2
             3             4
             5             6
             
a =
             3             4
             
A =
             1             2
             5             6

```




## string
**Description**
The sequence or array of characters.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`s = 'str'`|Uses *' '* to create a string named *s*.|
|`s = "str"`|Uses *" "* to create a string *s*. When using *" "* , the escape character will function. |
|`s = s_1 + s_2;`|Combinates the string *s_1* and string *s_2*.|

> When using *" "*, the escape character will functions. The following tabulation list normal escape characters  script library supports.


|Character | Description
|:---|:---|
|`\n` | line feed (LF) |
|`\t`| horizontal tab (HT) |
|`\f` | page feed (FF) |
|`\b` | backspace (BS) |
|`\r` | carriage return (CR) |
|`\a` | bell (BEL) |
|`\v `| vertical tabulation (VT) |
|`\\` | backslash |
|`\"` | double quotation marks |



**Example**
Example 1:

```

s = "aaa\nbbb"    # \n escape to newline
s2 = "ccc\"ddd"   # \" escape to "

```

Result:

```msf
s =
aaa
bbb  
s2 =
ccc"ddd 
```
Example 2:
```
s_1 = 'Hello';
s_2 = 'world';

s_3 = s_1 + ',' + s_2 + '!'

```

Result:

```msf
s_3 =
Hello,world!
```

**See also**
num2str, str2num

## struct
**Description**
`struct` uses filed-value pairs to group related data.
Used in FDTD and FDE.

**Synatx**
|Code|Function|
|:---|:---|
|`st= struct();`|Creates an empty struct.|
|`st = struct('field_name_1' : value_1, ... , 'field_name_n' : value_n);`|Creates a struct having n fields. The nth field is named *'field_name_n'* and its value is *value_n*.|
|`st = struct('field_name_1' : value_1; ... ; 'field_name_n' : value_n);`|Creates a struct having n fields. The nth field is named *'field_name_n'* and its value is *value_n*.|
|`st = struct('field_name_1' , value_1 , ... , 'field_name_n' : value_n);`|Creates a struct having n fields. The nth field is named *'field_name_n'* and its value is *value_n*.|
|`st = struct(field_name_1 = value_1, ... , field_name_n = value_n);`|Creates a struct having n fields. The nth field is named *'field_name_n'* and its value is *value_n*.|
|`st = struct(field_name_1 = value_1; ... ; field_name_n = value_n);`|Creates a struct having n fields. The nth field is named *'field_name_n'* and its value is *value_n*.|
|`v = struct_name.['field_name'];`|Gets the value of field named *'field_name'* in struct named  *'struct_ name'*.| 
|`v = struct_name.('field_name');`|Gets the value of field name *'field_name'* in struct named  *'struct_ name'*.|
|`v = struct_name.field_name;`|Gets the value of field name *'field_name'* in struct named *'struct_name'*.| 
|`struct_name.['field_name'] = new_value;`|Changes the value of the field named  *field_name* to *new_value*.|
|`struct_name.('field_name') = new_value;`|Changes the value of the  field named *field_name* to *new_value*.|
|`struct_name.field_name = new_value`|Changes the value of the field named *field_name* to *new_value*.|



**Example**
```msf
E = struct('name' : 'E_struct' ; Ex = 1 ; Ey = 0, Ez = 0);

printf("E.name = '%s' \n" , E.name);
printf("E.['Ex'] = %f", E.['Ex']);

```

Result :
```msf
E.name = 'E_struct' 
E.['Ex'] = 1.000000
```

**See also**
matrix, cell


## rmfield
**Description**
Removes the specified field of designated struct.
Used in FDTD and FDE.

**Synatx**
|Code|Function|
|:---|:---|
|`rmfield('struct_name', 'field_name');`|Removes the specified field of designated struct.|

**Example**
```msf
st = struct('var1':1, 'var2':2) # create a struct

rmfield(st, 'var1')

```

Result :
```msf
st =
  struct with fields:
    var1: 1
    var2: 2
val =
  struct with fields:
    var2: 2

```

**See also**
struct


## cell
**Description**
The `cell` data type can be seen as an array of data containers called cell. Each cell has its index and can store any type of data.
Used in FDTD and FDE.

**Synatx**
|Code|Function|
|:---|:---|
|`cells = cell(r, cl);`|Creates an empty cell with *r* rows and *cl* columns.|
|`cells = {c_data_11, ... , c_data_1n ; c_data_21, ... , c_data_2n ; ...};`|Creates a cell with designated data. The *,* symbol means the separation of different columns, while the *;* means the separation of different rows.|
|`celem = cl(m1: m2, n1: n2);`|Gets the set of cells in cell *cl* according to the indices. The cells  cl(m, n) (m = m1, m1+1, ..., m2; n = n1, n1+1, ..., n2 ) of *cl* will be used to construct a new cell array named *celem*.|
|`celem = cl{m, n}`|Gets the contents of the cell designated by indices in cell *cl*.|



**Example**
Example 1:
```msf
C = {1, 2, 3; 'text', rand(5,10,2), {11; 22; 33} };
C  # to print cell named 'C'
```
Result:
```msf
C =
  2x3 cell array:
    {     1}    {          2}    {       3}
    {'text'}    {5x10x2 real}    {3x1 cell}
```

Example 2:

```msf
c2 = cell(2,3);

c2  # to print cell c2

```

```
c2 =
  2x3 cell array:
    {0x0 real}    {0x0 real}    {0x0 real}
    {0x0 real}    {0x0 real}    {0x0 real}
    
   
```
Example 3:
```msf
C = {1, 2, 3; 'text', rand(5,10,2), {11; 22; 33} };

c1 = C(2, 1)
c2 = C{2, 1}

```
Result:
```msf
c1 =
  1x1 cell array:
    {'text'}
    
c2 =
text  
```

Example 4:
Use the existing cell array to construct a new cell array.

```msf
CellArray = {'first row', 'hello_1', 111; 'second row', 'hello_2', 222; 'thired row', 'hello_3', 333}

# use CellArray(1, 1), CellArray(1, 2), CellArray(2, 1), CellArray(2, 2) to create a new cell array 
SubCellArray = CellArray(1: 2, 1: 2)
```

Result:

```
CellArray =
  3x3 cell array:
    { 'first row'}    {'hello_1'}    {111}
    {'second row'}    {'hello_2'}    {222}
    {'thired row'}    {'hello_3'}    {333}
SubCellArray =
  2x2 cell array:
    { 'first row'}    {'hello_1'}
    {'second row'}    {'hello_2'}
```


**See also**  
matrix, struct

## num2str
**Description**
Converts a number object into a string object.
Used in FDTD and FDE.

**Syntax**
|Code |Function| 
|:---|:---|
|`s = num2str(x);` |Converts the number *x* into a string object.|
|`s = num2str(x, 'fm');` |Converts the number *x* into a string object using the format *'fm'*.|

**Example**

```msf
a = 2;

# to see the data type of a 
printf("the data type of a : %s \n", class(a));  

# to see the data type of a  # to see the data type of as 
as = num2str(a);
printf("the data type of as : %s \n", class(as));  

```
Result:
```msf
the data type of a : num 
the data type of as : string 

```


## str2num
**Description**
Converts character array to numeric array.
Used in FDTD and FDE.

**Syntax**
|Code |Function|
|:---|:---|
|`num_arr = str2num(chr_arr);` |Converts character array to numeric array. The input can include spaces, commas, and semicolons to indicate separate elements. If `str2num` cannot parse the input as numeric values, then it will print the error statement.|

**Example**

```msf
chr_arr = '100 200 300';

num_arr = str2num(chr_arr)

```

Result :
```msf
num_arr =
           100           200           300
```

## line continuation ( ... )
**Description**
Continues the current command on the following line.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`...`|Continues the current command on the following line.|

**Example**

The following two expressions are equivalent:

```msf
a = 1+2+3+4;

b = 1+2+3...
    +4;
```

Result :
```msf
a =
            10
            
b =
            10            

```


# dataset

The dataset is composed of data(i.e. attributes of the dataset) and coordinate axes(i.e. parameters of the dataset) defined by `matrixdataset` function, which is mainly used to manage build-in data in the software. 

A basic dataset's format including:

|data name	| type | dimensionality |
|:---|:---|:---|
|attribute | double or complex-data| parameters' meshgrid |
|parameter | double| 1 |

The following part introduces some basic operations about dataset such as creation, data addition, data query and units setting.  

## matrixdataset
**Description**
Creates an empty dataset. 
Dataset is a data structure consisting of attributes and parameters. For details, see `addparameter` and `addattribute`.
Used in FDTD and FDE.


**Syntax**
|Code| Function|
|:---|:---|
|`matrixdataset;`|Creates an empty dataset without a name.|
|`matrixdataset('dts_name');`|Create a dataset named *'dts_name'*. |

**Example**
Create a dataset named 'epsr'.

```msf
dataset=matrixdataset('epsr');

```

**See also**
dataset, addparameter, addattribute

## addparameter
**Description**
Add the specific parameters to the defined dataset.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`R.addparameter('p_name', p);`|Adds the parameter named *'p_name'*  to dataset *R*, whose value is *p*.|
|`R.addparameter('p1_name', p1, 'p2_name', p2, ...);`|Adds interdependent parameters (*p1_name*, *p2_name*, ... to the dataset *R*. |

**Example**
```msf
x = 3;
y = 4;
p1 = 1;
p2 = 2;
dataset = matrixdataset('test_dataset');
dataset.addparameter('x', 1:x);
dataset.addparameter('y', 1:y);
dataset.addparameter('p1', p1, 'p2', p2);
```
**See also**
addattribute


## addattribute
**Description**
Adds specific attributes to the defined dataset.
Used in FDTD and FDE.


**Syntax**
|Code| Function|
|:---|:---|
|`R.addattribute("a_name",a);`|Adds the scalar attribute named *a_name* whose value is  *a* to the dataset *R*.|
|`R.addattribute("a_name",ax,ay,az);`|Adds the vector attribute named *a_name* whose value is *a_vector* to the existing dataset *R*. The components of the vector are *ax*, *ay* and *az*. |

**Example**
```msf
x = 3;
y = 4;
z = 5;
p1 = 1;
p2 = 2;
dataset = matrixdataset('test_dataset');
dataset.addparameter('x', 1:x);
dataset.addparameter('y', 1:y);
dataset.addparameter('z', 1:z);
dataset.addparameter('p1', p1, 'p2', p2);
dataset.addattribute('attr_scalar', rand(x,y,z));
dataset.addattribute('attr_vector', rand(x,y,z), rand(x,y,z), rand(x,y,z));
```

**See also**
addparameter


## members
**Description**
Determines which attributes a variable has.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`members(var)`|Determines which attributes the variable *var* has.|


**Example**
```msf
a = ones(3,4);
members(a)

```

Result :
```msf
val =
nr  nc  n  class  type  storage  

```

**See also**
dot(.)

## .
**Description**
Views attributes of the specified variable.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`s = var.attr;`|Views attribute *attr* of the specified variable *var*.|

The following list lists the meaning of  default attributes:
|Attribute|Meaning|
|:---|:---|
|nr|number of rows of matrix|
|nc|number of columns of matrix|
|ndims|dimensions count(multidimensional matrix)|
|dims|dimension size(multidimensional matrix)|
|n|total number of matrix elements|
|nnz|number of non-zero elements(sparse matrix)|
|class|class of variable|
|type|type of variable|
|storage|storage mode of matrix|
|file|file path(user-function)|

**Example**
```msf
b = ones(3,4);
members( b )
b.nr # view rows of a

```

Result :
```msf
val =
nr  nc  n  class  type  storage  
val =
             3
```
**See also**
members





## setparameterunit
**Description**
Sets the unit to the defined parameter which means that variable is physically meaningful in the 'SI’ system. The setting is "number" by default.
*unit_type* includes: *'number'*, *'length'*, *'time'*, *'frequency'*.
Used in FDTD and FDE.


**Syntax**
|Code| Description|
|:---|:---|
|`R.setparameterunit('p_name', 'unit_type')`|Sets unit type to the parameter named *'p_name'*.|

**Example**
```msf
x = 3;
y = 4;
dataset = matrixdataset('test_dataset');
dataset.addparameter('x', 1:x);
dataset.addparameter('y', 1:y);
dataset.setparameterunit('x', 'length');
dataset.setparameterunit('y', 'length');
dataset.addattribute('attr', rand(x,y));
```


# global and local variable
## global
**Description**
Declares variables are global variables.
The `global` keyword allows you to modify variables outside the scope of a function. It is used to create a global variable and change it in a function
Used in FDTD and FDE.


**Syntax**

|Code|Function|
|:---|:---|
|`global(var_1, var_2,... , var_n )`|Declares variables *var_1*, *var_2*, ..., *var_n*  are global variables. |



**Example**
```
function fun()
    global(a,b); # use global variables
    a='fun_var1';
    b='fun_var2';
  

end;

# change global variable
a = 'var1'; 
b = 'var2'; 
  printf("%s \n %s \n", a, b ); 
# display
fun()

```
Result :
```msf    
  
var1 
 var2
```

## local 
**Description**
Declares variables are local variable of the function.
This keyword can only be used in a function to declare a variable as a local variable of a function. Although by default, variables within functions are local.
Used in FDTD and FDE.


**Syntax**
|Code|Function|
|:---|:---|
|`local(var_1, var_2,... , var_n )`|Declares variables *var_1*, *var_2*, ..., *var_n*  are local variables of the function. |


**Example**
```msf
    function fun()
        local(a,b);
        a='local_var1'; #define local variable
        b='local_var2';
        printf("%s\n%s\n",a,b);
    end;

    a='global_var1';    #define global variable
    b='global_var2';
    printf("%s\n%s\n",a,b); #display global variable
    fun();  #display local variable
```

Result :
```msf
    
    global_var1
    global_var2
    local_var1
    local_var2
    
 ```
 
## getglobalvariable
**Description**
Gets the value of designated global variable.
Used in FDTD and FDE.

**Syntax**

|Code|Function|
|:---|:---|
|`getglobalvariable('var_name');`|Gets the value of designated global variable.|

**See also**
global, local

 
## static variable
**Description**
Defines a variable whose scope is the current file.
This keyword is used to define static variables, which only act in the current file. It can even be used inside functions, but it cannot be accessed outside the current file.
Used in FDTD and FDE.


**Syntax**

|Code|Function|
|:---|:---|
|`static(var_1, var_2, ... , var_n);`|Defines the variables *var_1, var_2, ... , var_n* are static variables.|


**Example**

```msf
    static(a);            # define static variables
    function fun1()
        printf("a:%s\n",a);
        a='fun1_changed'; # changed in fun1
    end;
    
    function fun2()
        printf("a:%s\n",a);
        a='fun2_changed'; # changed in fun2
    end;

    a='this_changed';
    fun1();
    fun2();
    printf("a:%s\n",a);
```

Result :

```msf
    
    a:this_changed
    a:fun1_changed
    a:fun2_changed
    
```

# Special constants
## constants
**Description**
The script library has defined some normal frequently-used mathematical and physical constants, which can be used without definition beforehand. To reuse those constants, you should redefine them in script.
Used in FDTD and FDE.

The following tabulation shows the constants script library provides:


|Symbol|Command	|Value | Unit | Interpretation|
|:---|:---|:---|:---|:---|
|$\pi$|pi| 3.14159265359| | the number $\pi$  |
|$c$ |c| 2.99792458e8 | $m \cdot {s^{-1}}$| the speed of light in the vacuum  | 
|$\varepsilon0$|eps0| 8.8541878128e-12|$F \cdot {m^{-1}}$ |the permittivity of free space  |
|$\mu0$|mu0| 1.25663706212e-6 | $N \cdot {A^{-2}}$ | the permeability of free space  |
|$h$ |h| 6.62607015e-34|$J\cdot s$ | the Planck constant  |
|$\hbar$|hbar| 1.054571800e-34 | $J\cdot s$ | the reduced Planck constant  |
|$e$|e| 1.602176634e-19 |$C$ | 	the electron volt  |



## characters
There are some special characters in the script library. In some situations, special characters can be convenient and useful.
Used in FDTD and FDE. 
 
|Character | Description|
|:---|:---|
|inf| infinity |
|nan| Not a Number  |
|-0 | negative zero |
|\# | Coments line  |
|%% | Create a illegal variable's name |
|$$ | A struct contains all global variables and functions |

