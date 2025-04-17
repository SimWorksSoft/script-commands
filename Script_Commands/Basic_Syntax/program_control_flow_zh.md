---
title: 程序控制流程
description: This section describes the most commonly used key words to control the program flow.
keywords: Flow control,Conditional statement,Exception processing,If,While,For,Break,Loop,Try,Catch
businessId: Script-Commands_program-control-flow
language: zh-CN
sort: 264
published: true
date: 2024-02-07T09:03:02.633Z
tags: program control flow, basic synatx
editor: markdown
dateCreated: 2022-12-13T07:15:13.580Z
---

**This section describes the functions to control the program flow.**


# if
**Description**
If the condition is true, executes statements.
Used in FDTD and FDE.

**Syntax**
(1) If the expression is true, executes statements.
```msf
if expression
    statements
end
```
(2) If the expression is true, executes statements_1. Otherwise, execute statements_2.
```msf
if  expression
    statements_1
else
    statements_2
end
```

(3)If the expression_k is true, executes the statements_k.

```msf
if expression_1
    statements_1
elseif expression_2
    statements_2
...
elseif expression_k
    statements_k
else
    statements_k+1
end
```


**Example**  
```msf
if  0
    'true-1'
elseif 0
    'true-2'
elseif 1
    'true-3'
else
    'else-part'
end 
```

Result:

```msf
val =
true-3
```
**See also**
while, for

# while
**Description**
While the expression is true, executes the statement.
Used in FDTD and FDE.

**Syntax**
While the expression is true, executes the statement.
```msf
while expression
    statement;
end
```
**Example**  
```msf
i = 0;
while i <= 5
    printf("i = %d\n", i);
    i = i + 1;
end
```

Result:
```msf
i = 1
i = 2
i = 3
i = 4
i = 5

```
**See also**
if, for

# for
**Description**
Executes the statements for each element that meets the requirement.
Used in FDTD and FDE.

**Syntax**
```msf
for element = values
    statements;
end

```

**Example**  
```msf
x = ["a", "sample", "string"];
for i = x
    printf ("%s ", i); 
end
```
Result:
```msf
a sample string 
```
**See also**
if, while


# break
**Description**
Breaks the `for` or `while` loop, the code after `break` sentence will not be execute.
Used in FDTD and FDE.

**Syntax**
Breaks the `for` or `while` loop.
```
break;
```
**Example**  
```msf
for  i = 1:100
    
    if i == 3 
        break;
    end
    printf("i = %d\n", i);
end


```
Result:
```msf
i = 1
i = 2
```

**See also**
continue


# continue
**Description**
Terminates the current iteration and starts the next iteration of `for` or `while` loop.
Used in FDTD and FDE.

**Syntax** 
The `continue` statement forces execution of the next iteration of the inner-most `for` or `while` loop to begin immediately. 
```
continue;
```

**Example**  
```msf
for  i = 1:4
    
    if i == 2
        continue;
    end
    printf("i = %d\n", i);
end
```
Result:
```msf
i = 1
i = 3
i = 4
```
**See also**
break
 

# try, catch
**Description**
Executes statements and catches resulting errors.
Used in FDTD and FDE.

**Syntax**
|Code| Function |
|:---|:---|
|`try`|Executes commands in the `try` block and checks errors.|
|`catch`|Catches the error messages from `try` block and processes error messages according to the `catch` block.|

Runs the block of commands. If an error occurs, the error message is not displayed and the script continues.
```msf
try 
    commands;

end
...
```

Runs the block of commands *commands_1*. If an error occurs, the error message is stored in the variable "error_message" and program control goes immediately to the `catch` block.

```msf
try
    commands_1;

catch error_message

    commands_2;

end
```


**Example**  

Example 1:
```msf
# test code:
try
  a
catch exception
  D=4;
end

exception # show exception
```

Result:
```msf
exception =
'a' is undefined function or variable

```

Example 2:

```msf
# test code:
try
    'before error'
    a
    'after error'
end
```
Result:
```msf
val =
before error  
```



