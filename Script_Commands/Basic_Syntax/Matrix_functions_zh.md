---
title: 矩阵运算
description: The section introduces the functions used in linear algebra and solving equations.
keywords: Matrix calculation,Linear algebra,Solve equation,Determinant,Singular value decomposition(svd),Eigenvalue 
businessId: Script-Commands_matrix-calculations
language: zh-CN
sort: 268
published: true
date: 2024-02-07T08:58:59.603Z
tags: 
editor: markdown
dateCreated: 2024-01-05T07:45:04.364Z
---

**The section introduces the functions used in linear algebra and solving equations.**

# Linear Algebra
## inv
**Description**
Computes the inverse of a matrix.
Used in FDTD and FDE.

`inv( A )` computes the inverse of A. The `inv` function, because it uses the `solve` function, uses a symmetric/hermitian solver if the coefficient matrix is symmetric/hermitian.


**Syntax**
|Code|Function|
|:---|:---|
|`out = inv(P);`|Computes the inverse of a matrix *P*.|


**See also**
pinv

## pinv
**Description**
Computes the Moore-Penrose pseudoinverse.
Used in FDTD and FDE.

**Syntax**
|Code|Fucntion|
|:---|:---|
|`pinv(A);`|Computes the Moore-Penrose pseudoinverse.|
|`pinv(A, tolerance);`|Computes the Moore-Penrose pseudoinverse according to the tolerance setting. If a singular value of A is smaller than tolerance, it will be treated as 0. |

**See also**
inv


## trace
**Description**
Computes the trace of a matrix.
Used in FDTD and FDE.

**Syntax**
|Code|Fucntion|
|:---|:---|
|`out = trace( A );`|Computes the trace of a matrix *A*.|

**See also**
diag

## rcond
**Description**
Condition number.
Used in FDTD and FDE.

`rcond` computes an estimate of the condition number of the input matrix, A. `rcond()` uses the LAPACK routines DGECON, or ZGECON. Probably the most published way to compute the condition of a matrix is: Kcond = ||A|| * ||inv(A)||. Another method is to use the 1st and last singular values of *A*, Kcond=sigma(1)/sigma(n); `rcond` computes an ESTIMATE of the condition number without computing all of the columns of `inv(A)`. For more information see the LAPACK User's Guide.

**Syntax**
|Code| Function|
|:---|:---|
|`C=rcond(A);`|Computes an estimate of the condition number of the input matrix *A*.|


## det
**Description**
Matrix determinant.
Used in FDTD and FDE.

`det` computes the determinant of the matrix argument. `det` uses the LAPACK functions to factor the input, and the LINPACK algorithm to calculate the determinant.

**Syntax**
|Code| Function|
|:---|:---|
|`D=det(A);`|Computes the determinant of the matrix *A*.|

**Example**

```msf
a=[1 ,   2 ,  4;
   7,   4 ,  8;
   2 ,   3 ,  9];
d=det(a) 
```
Result:
```msf
d =
           -30 
```

## rank
**Description**
Rank of matrix.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`k=rank(A);`| Returns the rank of matrix *A*.|
|`k=rank(A,tol);`|Specifies a different tolerance to use in the rank computation. The rank is computed as the number of singular values of *A* that are larger than *tol*.|

**Example**

```msf
a=[1 ,   2 ,  4;
   7,   4 ,  8;
   2 ,   3 ,  9];
k=rank(a) 
```
Result:
```msf
k =
             3  
```


## tril
**Description**
Returns the lower triangular part of A.
Used in FDTD and FDE.

**Syntax**
|Code|Fucntion|
|:---|:---|
|`out = tril( A );`|Returns the lower triangular part of *A*.|
|`out = tril( A, K );`|Returns the elements on and below the K-th diagonal of *A*. K = 0: main diagonal; K > 0: above the main diag; K < 0: below the main diag.|

**See also**
triu

## triu
**Description**
Returns the upper triangular part of A.
Used in FDTD and FDE.

**Syntax**
|Code|Fucntion|
|:---|:---|
|` out = triu( A );`|Returns the upper triangular part of A.|
|`out = triu(x; k);`| Returns the elements on and above the k-th diagonal of A.  K = 0: main diagonal; K > 0: above the main diag; K < 0: below the main diag.|

**See also**
tril

## symm
**Description**
`symm(A)` is the symmetric (Hermitian) part of A, (A+A')/2. It is the nearest symmetric  (Hermitian) matrix to A in both the 2- and the Frobenius norms.
Used in FDTD and FDE.

**Syntax**
|Code|Fucntion|
|:---|:---|
|`ret = symm ( A )`|Returns the symmetric part of a matrix.|

**Example**
```msf
A = [1 + 2i, 2 + 5i;...
     3 + 7i, 4 + 1i ]

A_symm = symm(A)

# A_symm is a Hermitian matrix
D = A_symm - conj(A_symm.') # or D = A_symm - A_symm'
```

Result:
```
A =
              1 +           2i              2 +           5i
              3 +           7i              4 +           1i
A_symm =
              1 +           0i            2.5 -           1i
            2.5 +           1i              4 +           0i
D =
              0 +           0i              0 +           0i
              0 +           0i              0 +           0i
```


## permute
**Description**
Rearranges dimensions of N-D array.
Used in FDTD and FDE.

This function can rearrange dimensions of a matrix according to the specified order, which can be seen as the generalization of transposition. All the elements of the input *Order* must be unique, real, positive, integer values. 
If the input *Order* is [k, m, n, ... ], the size of the output matrix *B* will be k * m * n * ... .
And the ith dimension of the output matrix *B* is the Order(i)th dimension of the input matrix *A* .


**Syntax**
|Code|Fucntion|
|:---|:---|
|` B = permute(A, order);`|Rearranges dimensions of N-D array.|

**Example**
```msf
# create matrix A
A = [1, 2, 3;...
    -2, 5, -3 ];
 
# use permute to transpose matrix A
# the 1st dimension of B is the 2nd (Order(1)) dimension of A
# the 2nd dimension of B is the 1st (Order(2)) dimension of B 
Order = [2, 1]; 
B =  permute(A, Order)    
```

Result:
```
A =
             1             2             3
            -2             5            -3
B =
             1            -2
             2             5
             3            -3
```

## sparse
**Description**
Converts full (dense) storage to sparse storage.
Used in FDTD and FDE.


`sparse` converts its argument from a dense storage format to the sparse storage format. If the argument is already sparse, then it is condensed (any non-zeros are removed). The sparse storage format is commonly referred to as sparse row-wise storage. Only the non-zero elements of the matrix are stored in a row-wise fashion. Row-wise storage is used for several reasons:
- The matrix vector product A * x is a very common operation, efficiently performed with row-wise storage.
- Row-wise (and column-wise) storage is a very general storage scheme that works well for general non-symmetric matrices. There is a penalty to pay for storing symmetric matrices in this fashion, but it is small.


Rlab does not attempt to out-smart the user by automatically converting sparse matrices to dense matrices, or vice-versa. Even if the user explicitly fills the  sparse matrix so that the number of non-zeros is equal to the full size of the matrix, the sparse storage format is retained.

Certain operations on sparse matrices will return dense matrices. For instance, the cosine operation on a sparse matrix will create a dense matrix with ones where there used to be zeros.

Sparse matrices are printed differently than full, or dense matrices. Only the non-zero elements are printed, along with their row and column values. 

**Syntax**
|Code| Function|
|:---|:---|
|`out = sparse( A );`|Converts full (dense) storage to sparse storage.|


**Example**
```msf
a = [0, 1, 0;
     2, 0, 0;
     0, 0, 3];
s = sparse(a)
```
Result:
```msf
s =
 (1, 2)    	           1
 (2, 1)    	           2
 (3, 3)    	           3
```
**See also**
spconvert, full

## spconvert
**Description**
Converts a full column matrix to sparse storage.
Used in FDTD and FDE.

`spconvert` converts its argument to, or from, the sparse storage format. If the argument is a 3 (or 4) column full matrix, the argument is converted to sparse storage format. The 1st two columns are taken as the row and column indices for the elements in the third column. The rows of the input matrix do not have to be in any particular order. If there are duplicate elements (same row and column number), then they are summed.

If the argument is a sparse matrix, then it is converted to a full matrix with 3 columns. The first two columns are the row and column indices of each non-zero element, and the third column contains the corresponding element values (columns 3 and 4 if the matrix is complex).

**Syntax**
|Code| Function|
|:---|:---|
|`out = spconvert ( A );`|Converts a full column matrix to sparse storage.|


**Example**
Creates a sparse matrix of zeros with 1000 rows, and 1000 columns.

```msf
s = spconvert([ 1000, 1000, 0 ])
show(s);
```
Result:
```msf
s =
	[all zeros]
	nr                  :	1000
	nc                  :	1000
	n                   :	1e+06
	nnz                 :	0
	class               :	num
	type                :	real
	storage             :	sparse
```

**See also**
sparse, full


## full
**Description**
Converts sparse storage to full (dense) storage.
Used in FDTD and FDE.

`full` converts its argument from the sparse storage format to the full, or dense, storage format.

**Syntax**
|Code|Fucntion|
|:---|:---|
|`out = full( A );`|Converts its argument from the sparse storage format to the full, or dense, storage format.|



**Example**
```msf
d = [1, 1, 10; 2, 4, 20; 3, 1, 12; 5, 2, 13; 1, 4, 3]
s = spconvert(d)
f = full(s)
```

Result:
```msf
d =
             1             1            10
             2             4            20
             3             1            12
             5             2            13
             1             4             3
s =
 (1, 1)    	          10
 (1, 4)    	           3
 (2, 4)    	          20
 (3, 1)    	          12
 (5, 2)    	          13
f =
            10             0             0             3
             0             0             0            20
            12             0             0             0
             0             0             0             0
             0            13             0             0
```

**See also**
sparse, spconvert

## diag
**Description**
Constructs diagonal matrix using input argument.
Used in FDTD and FDE.

If the 1st argument A is a 1xN matrix, constructs a diagonal matrix from the input. Optionally if K (scalar) is specified then create a matrix with the vector as the Kth diagonal.

>K = 0, the elements of input are arranged on the main diagonal.
>K < 0, the elements of input are arranged below the main diagonal.
>K > 0, the elements of input are arranged above the main diagonal.

If the 1st argument is a MxN matrix, constructs a 1xN matrix from the diagonal elements of the input matrix. Optionally if K is specified return the vector from the Kth diagonal of the input matrix.

>K = 0, the elements of the newly constructed vector are from the main diagonal of the input.
>K < 0, the elements of the newly constructed vector are from the diagonal below the main diagonal of the input.
>K > 0, the elements of the newly constructed vector are from the diagonal above the main diagonal of the input.


**Syntax**
|Code|Function|
|:---|:---|
|`out = diag( A );`|If the 1st argument, A is a 1xN matrix, constructs a diagonal matrix from the input. If the 1st argument is a MxN matrix, constructs a 1xN matrix from the diagonal elements of the input matrix.|
|`out = diag( A, K );`|If the 1st argument, A is a 1xN matrix, constructs a diagonal matrix from the input with the vector as the Kth diagonal. If the 1st argument is a MxN matrix, constructs a 1xN matrix from the diagonal elements of the input matrix from the Kth diagonal of the input matrix.|

**Example**

```msf
# create matrix A
A = [1, 2, 3 ];

# use A to construct a new matrix 
# and the elements of A are arranged on the main diagonal 
B_onMainDiag = diag(A, 0)

# use A to construct a new matrix and
# the elements of A are arranged on the first diagonal above the main diagonal
B_aboveMainDialog = diag(A, 1)

# use A to construct a new matrix and
# the elements of A are arranged on the second diagonal below the main diagonal
B_belowMainDialog = diag(A, -2)
```

Result:

```
B_onMainDiag =
             1             0             0
             0             2             0
             0             0             3
B_aboveMainDialog =
             0             1             0             0
             0             0             2             0
             0             0             0             3
             0             0             0             0
B_belowMainDialog =
             0             0             0             0             0
             0             0             0             0             0
             1             0             0             0             0
             0             2             0             0             0
             0             0             3             0             0
```


**See also**
tril, triu


## factor
**Description**
Factors a square matrix.
Used in FDTD and FDE.

The `factor` function computes the LU factorization of the input matrix A. `factor` returns 3 elements.


**Syntax**
|Code| Function|
|:---|:---|
|`[LU, Pvt, Rcond] = factor(A);`|If A is a general matrix, returns a matrix *LU* containing the LU factors, a vector *Pvt* containing the pivot indices, and the inverse of the condition estimate *Rcond*.|
|`[Ldl, Pvt, Rcond] = factor(A);`|If A is a symmetric matrix, returns a matrix *Ldl* containing the block diagonal matrix *D*, and the multipliers used to obtain *L*. The *Pvt* and *Rcond* are the same as above.|

The user can override `factor`'s choice of solution type with the optional argument 'TYPE'.
|Code| Function|
|:---|:---|
|`[LU, Pvt, Rcond]=factor(A, 'TYPE');`|'TYPE' can be 'g' or 'G', means the general solution is used.
|`[Ldl, Pvt, Rcond]=factor(A, 'TYPE');`|'TYPE' can be  's' or 'S', means the symmetric solution is used.|

`factor` utilizes the LAPACK subroutines DSYTRF, DSYCON or ZHETRF, ZHECON.
`factor` returns the results in the above format, so that they may be conveniently used with `backsub` for repetitive solutions. The user-function `lu` will separate the results from `factor` into separate L and U matrices.

**Example**

```msf
A = [10, -7, 0;
     -3,  2, 6;
      5, -1, 5];

[LU, Pvt, RCond] = factor(A);
[L, U, P] = lu(A);
# LU is combined from matrix L and matrix U.
L
U
LU
```

Result: 

```
L =
             1             0             0
           0.5             1             0
          -0.3         -0.04             1
U =
            10            -7             0
             0           2.5             5
             0             0           6.2
LU =
            10            -7             0
           0.5           2.5             5
          -0.3         -0.04           6.2
```


## svd
**Description**
Singular Value Decomposition.
Used in FDTD and FDE.

The output is a struct containing the three afore-mentioned objects (u, sigma, v).  Various forms of the right and left singular vectors can be computed, depending upon the value of the second, optional, string argument. 

**Syntax**
|Code| Function|
|:---|:---|
|`[u,sigma,v]=svd(A)`|Computes the singular values of the input matrix A, along with the right and left singular vectors in their minimal form. Where, A = U * sigma* V'.|
|`[u, sigma, v]=svd(A, 'TYPE');`|Computes the singular vectors in designated form. 'TYPE' can be *'S'* (a minimal version of U, and V are returned, this is the default), *'A'* (the full U, and V are returned) or *'N'* (U and V are not computed, empty U and V are returned).|

**Example**

```msf
A = [0.96, 1.72; 2.28, 0.96];
[u,sigma,v] = svd(A)
```
Result:
```msf
u =
          -0.6          -0.8
          -0.8           0.6

sigma =
             3             0
             0             1

v =
          -0.8           0.6
          -0.6          -0.8
```

## hess
**Description**
Finds the Hessenberg form of a matrix.
Used in FDTD and FDE.

Produces a unitary matrix P and a Hessenberg matrix H so that:
$$A = P * H * P^{'} \\ P^{'} * P = eye(size(P)) $$


**Syntax**
|Code|Function|
|:---|:---|
|`[P,H]=hess(A);`|Produces a unitary matrix P and a Hessenberg matrix H.|


**Example**

```msf
a = [2,3,1;45,3,5;8,9,6]
[p,h] = hess(a)

p*h*(p.')

p*p.'

```
Result:
```msf
a =
             2             3             1
            45             3             5
             8             9             6
p =
             1             0             0
             0  -0.984562508  -0.175033335
             0  -0.175033335   0.984562508

h =
             2   -3.12872086   0.459462504
   -45.7055795    5.50454763   -5.08808042
             0   -9.08808042    3.49545237
val =
             2             3             1
            45             3             5
             8             9             6
val =
             1             0             0
             0             1             0
             0             0             1
```

## balance
**Description**
Balances a matrix for equal row and column norms.
Used in FDTD and FDE.

`balance` uses the LAPACK subroutines DGEBAL and ZGEBAL to balance the input matrix so that the row and column norms are approximately equal. `balance` returns t and ab.

**Syntax**
|Code|Function|
|:---|:---|
|`[t,ab]=balance(A);` |Balances a matrix for equal row and column norms.|

**Example**
```msf
a =[ 0,  0, 1, 0;0,0,0,1;11,10,0,0;10,11,0,0]
   

[t,ab] = balance(a)

inv(t)*a*t - ab
```

Result:
```msf
a =
             0             0             1             0
             0             0             0             1
            11            10             0             0
            10            11             0             0
t =
             1             0             0             0
             0             1             0             0
             0             0             1             0
             0             0             0             1

ab =
             0             0             1             0
             0             0             0             1
            11            10             0             0
            10            11             0             0
            
val =
             0             0             0             0
             0             0             0             0
             0             0             0             0
             0             0             0             0            
```

Only square matrices are allowed.


## qr
**Description**
QR decomposition.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`[Q,R]=qr(A);` |Computes the QR decomposition of the input matrix A such that: A=Q * R.|
|`[Q,R,P]=qr(A,'p');` |Produces unitary Q, upper triangular R and a permutation matrix P so that A * P = Q * R.|


**Example**

```msf
a=[1, 2, 1, 1; 1, 1, 1, 1; 11, 10, 1, 1; 10, 11, 1, 1]
[q,r] = qr(a);

q*r
```
Result:
```msf
a =
             1             2             1             1
             1             1             1             1
            11            10             1             1
            10            11             1             1
val =
             1             2             1             1
             1             1             1             1
            11            10             1             1
            10            11             1             1
```

## schur
**Description**
Schur decomposition.
Used in FDTD and FDE.

The `schur` function returns t and z, such that:
$$A = z * t * z'$$

**Syntax**
|Code|Function|
|:---|:---|
|`[z,t]=schur(A);`| If A is real, the t is in "Real-Schur" form. The "Real-Schur" form is block upper-triangular with 1-by-1 and 2-by-2 diagonal blocks; each 2-by-2 diagonal block has its diagonal elements equal and its off-diagonal elements of opposite sign. The eigenvalues of the 2-by-2 block: [a, b; c, a] are: a +/- sqrt(b * c). |

**Example**

```msf
a=[1, 2, 1, 1; 1, 1, 1, 1; 11, 10, 1, 1; 10, 11, 1, 1]
       
[z,t] = schur(a);

z * t * z.'
```
Result:
```msf
a =
             1             2             1             1
             1             1             1             1
            11            10             1             1
            10            11             1             1
val =
             1             2             1             1
             1             1             1             1
            11            10             1             1
            10            11             1             1 
```


## chol
**Description**
Cholesky factorization, uses the LAPACK subroutine DPOTRF and ZPOTRF.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`U=chol(A)`| Computes the Cholesky factorization of the input matrix. The input matrix must be real symmetric positive definite, or complex Hermitian positive definite.| 

`chol()` produces an upper triangular matrix $U$, where $U'* U = A$.

**Example**

```msf
a = [    54,           36,           78  
         36,           29,           67  
         78,           67,          161  ]

u=chol(a);

u.' * u
```
Result:
```msf
a =
            54            36            78
            36            29            67
            78            67           161
val =
            54            36            78
            36            29            67
            78            67           161
 
```

## lu
**Description**
Computes the L and U factors of the matrix A.
Used in FDTD and FDE.

The function `lu` is a user-function that utilizes the built-in function `factor`. `factor` does the factorization using the LAPACK functions DGETRF/ZGETRF, and DGECON/ZGECON.

**Syntax**
|Code| Function|
|:---|:---|
|`[L, U, P] = lu (A)`|Computes the "LU" factors of the input matrix *A*. The input matrix must be square. `lu()` returns L, U, P. The factorization has the form: A = P'\*L\*U.|

**Example**

```msf
A = [17    24     1     8    15
    23     5     7    14    16
     4     6    13    20    22
    10    12    19    21     3
    11    18    25     2     9]

[L, U, P] = lu(A);

P.' * L * U
```
Result:

```msf
A =
            17            24             1             8            15
            23             5             7            14            16
             4             6            13            20            22
            10            12            19            21             3
            11            18            25             2             9
 

val =
            17            24             1             8            15
            23             5             7            14            16
             4             6            13            20            22
            10            12            19            21             3
            11            18            25             2             9

```



## eig
**Description**
Computes the eigenvectors and eigenvalues of the input matrix.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`[vec, val]=eig(A);`| Returns *val* and *vec* which are the eigenvalues and eigenvectors of matrix *A*. `eig` checks for symmetry in *A*, and uses the appropriate solver.|
|`[vec, val]=eig(A, B);`|Computes the eigenvectors and eigenvalues of *A* and *B*. Where A * x=lambda * B * x. The eigenvalues and eigenvectors are returned in *val* and *vec*. `eig` checks for symmetry in *A* and *B* and uses the appropriate solver. Uses the LAPACK subroutines DSYEV/ZHEEV or DGEEV/ZGEEV.|
|`e=eig(A);`|Returns a column vector containing the eigenvalues of matrix *A*.|
|`e=eig(A, B);`|Returns a column vector containing the generalized eigenvalues of matrices *A* and *B*.|

**Example**

The generalized eigenvalue problem arises quite regularly in structures. From the second order differential equations describing a lumped mass system arise $M$ and $K$, coefficient matrices representing the mass and stiffness of the various physical degrees of freedom. The equations are formulated as follows:

$$ M * dx^2/dt^2 + K * x = F $$
          
Which leads to the eigenvalue problem:

$$K*v = w^2 * M * v$$
       
For a two degree of freedom system we might have:

```msf
m = eye(2,2);
k = [5,1;1,5];
[vec , val] = eig(k, m);
          
# Test the solution
          
k * vec[:,1]    
val[1] * m * vec[:,1]
``` 

Result:
```msf
val =
   -2.82842712
    2.82842712
val =
   -2.82842712
    2.82842712
```

Show the properties of the solution.
```msf
          
# Properties of the solution

vec' * m * vec
 
          
vec' * k * vec

```
Result:
```msf
val =
             1             0
             0             1
val =
             4             0
             0             6
```

The eigenvalues and eigenvectors are sometimes obtained by converting the generalized problem into a standard eigenvalue problem (this is only feasible under certain conditions).


## mnorm
**Description**
Computes the matrix norm.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`N=mnorm(A);`| Computes the 1-norm of the input matrix. |
|`N=mnorm(A,'TYPE' );`|Computes the matrix norm. The input parameter *'TYPE'* allows the user to specify the desired type of matrix norm with a string argument. The details about *'TYPE'*  can be seen below.|

The input parameter *'TYPE'* that can be used:
- M or m
Returns max(abs( A )).

- 1, O or o
Returns the 1-norm (default), the largest column `max(sum(abs(A)))`.

- 2
Returns the matrix 2-norm (largest singular value).

- I or i
Returns the infinity-norm, the largest row `max(sum(abs(A')))`.

- F, f, E or e
Returns the Frobenius norm.

LAPACK subroutines DLANGE and ZLANGE are used to compute all norms, except the 2-norm.

*Note:* If *'TYPE'* is Inf (the output from `inf()`, for example), then `norm` will compute the Infinity norm of the matrix *A*.

**See also**
vpnorm

## vpnorm
**Description**
Computes the vector P norm.
Used in FDTD and FDE.

`vpnorm` computes the vector P-norm of V. The second argument is required, and specifies the value of P.

A small Rlab program demonstrating the P-norm computation is provided below. However, `vpnorm` is implemented as a builtin function for maximum efficiency.

```msf
function pnorm = Pnorm( V , P )
    pnorm =  (sum ( V.^P )).^(1/P);
end;
```

**Syntax**
|Code| Function|
|:---|:---|
|`out = vpnorm ( V , P );`|`vpnorm` computes the vector P-norm of V. The second argument is required, and specifies the value of P.|

**Example**

```msf
# Cauchy Inequality
a = rand(3, 1);
b = rand(3, 1);

D_InEql = dot(a, b) - vpnorm(a, 2)*vpnorm(b, 2)

# There exists a constant t > 0 such that d_i= t * c_i, (i = 1，2, 3), so the inequality will be an equality.
c = rand(3, 1);
d = 2 * c;
D_Eql = dot(c, d) - vpnorm(c, 2)*vpnorm(d, 2)
```

Result:
```
D_InEql =
  -0.212200821
D_Eql =
-4.4408921e-16
```


## norm
**Description**
Computes the matrix or vector norm.
Used in FDTD and FDE.

This function is a cover-function for the two builtin functions `mnorm()`, which computes matrix-norms, and `vpnorm()`, which computes vector P-norms.

**Syntax**
|Code| Function|
|:---|:---|
|`N=norm(A);`|Computes the 2-norm of the input vector.|
|`N=norm(A,B);`|Computes the matrix or vector norm. The second input parameter *B* allows the user to specify the desired type of matrix norm. The details about *B* can be seen below.|

If A is a matrix, valid B arguments are:
- 1
Returns  `max(sum(abs(A)))`.

- 2
Returns `max(svd(A))`.

- inf
Returns `max(sum(abs(A')))`.

- 'fro'
Returns `mnorm(A,'F')`.

If A is a vector(either row or column), valid B arguments are:

- 1
Returns `sum(abs(A))`.

- 2
Returns `sum(abs(A)\.^2 )^(1/2)`.

- p
Returns `sum(abs(A)\.^p )^(1/p)`.

- inf
Returns `max(abs(A))`.

- \- inf
Returns `min(abs(A))`.

- 'fro'
Returns `sqrt(sum(diag(S * S')))`.

LAPACK subroutines DLANGE and ZLANGE are used to compute all norms, except the 2-norm.

*Note:* If *B* is `inf` (the output from `inf()`, for example), then norm will compute the infinity norm of the matrix *A*.

**Example**
Example 1:
```msf
X = [2 0 1;-1 1 0;-3 3 0;-3 3 0];
n = norm(X)
n = norm(X,1)
n = norm(X,2)
n = norm(X,inf)
# sparse matrix
X = diag(ones(1,5));
n = norm(X,'fro')
```
Result 1:
```msf
n =
    6.33730681
n =
             9
n =
    6.33730681
n =
             6
n =
    2.23606798
```



Example 2:
```msf
X = sin([2 0 1 -1 1 0]);
n = norm(X)
n = norm(X,1)
n = norm(X,2)
n = norm(X,5)
n = norm(X,inf)
n = norm(X,-inf)
n = norm(X,'fro')
```

Result 2:
```msf
n =
    1.71785973
n =
    3.43371038
n =
    1.71785973
n =
    1.13544885
n =
   0.909297427
n =
             0
n =
    1.71785973
```

**See also**
mnorm

# Solving Equations

## solve
**Description**
Solves linear equations.
Used in FDTD and FDE.


`solve` solves a system of linear equations:
$$A * X = B$$

*A*  is the coefficient matrix. *B* is the right hand side. *X* is the solution.
`solve` uses the LAPACK subroutines DGETRF, and ZGETRF if *A* is general. `solve` uses the LAPACK subroutines DSYTRF, and ZHETRF if *A* is symmetric.

**Syntax**
|Code| Function|
|:---|:---|
|`X=solve(A,B);`| Solves a system of linear equations:$A * X = B$.  *B* can contain multiple right-hand-sides, one in each column. `solve` returns a matrix of the solutions, *X*, where each column of the solution corresponds to a column of *B*.|
|`X=solve(A, B, 'TYPE');`|Solves a system of linear equations. The  third and optional argument *'TYPE'* allows the user to use different solve mode, the details can be seen below.|

The third and optional argument *'TYPE'* allows the user to override the symmetry check, and force the `solve` to use either the general or the symmetric solver:

- If *TYPE* is 'g' or 'G', the general solution is used.
- If *TYPE* is 's' or 'S', the symmetric solution is used.

**Example**

```msf
A = [1, 0;1, 1]

B = [2; 3]

X = solve(A, B)

Pr = A * X
```

Result: 

```msf
A =
             1             0
             1             1
B =
             2
             3
             
X =
             2
             1
Pr =
             2
             3
```


## sylv
**Description**
Solves the Sylvester matrix equation.
Used in FDTD and FDE.

**Syntax**
|Code|Function|
|:---|:---|
|`X=sylv(A,B,C);`|Solves the Sylvester equation $A*X+X*B=C$. The method forms the single vector equation using Kronecker products.|


  
## poly
**Description**
Converts roots to polynomial.
Used in FDTD and FDE.

**Syntax**
|Code| Function|
|:---|:---|
|`p = poly(V);`| When *V* is a vector, returns the coefficients of a polynomial, where each root of the polynomial is an element of *V*.|
|`p = poly(A);`|When *A* is a n-order square matrix, returns N + 1 coefficients of characteristic polynomial of the matrix, $det(λI -A)$.|

**Example**
Example 1:

```msf
# example 1
A = [1 2 3; 4 5 6; 7 8 0];
p = poly(A)
```
Result:
```msf
p =
             1            -6           -72           -27
```
Example 2:

```msf
# example 2
A = [1 8 -10; -4 2 4; -5 2 8];
p = poly(A);  
e = eig(A);

deg = length(p);

r = e(1);
y = 0;


for k = 1 : deg
    
    y = y +  p(deg + 1 - k) * (r^(k-1));
            
end    
  
y  
```
Result:
```msf
y =
  -1.136868377e-12 +              0i
```

## lyap
**Description**
Solves the general form of the Lyapunov (Sylvester) equation.
Used in FDTD and FDE.

`lyap` solves the general form of the Lyapunov (Sylvester) equation:

$$ A* X + X * B = -C $$

       
To solve the special form of the Lyapunov equation:

$$ A*X + X*A' = -C $$
  

We can use this method: `lyap (A,A',C)`.
**Syntax**
|Code|Fucntion|
|:---|:---|
|`out = lyap ( A , B , C ); `|Solves the general form of the Lyapunov (Sylvester) equation.|

**See also**
schur, sylv  

## backsub
**Description**
Solution of $Ax = B$ by backsubstitution.
Used in FDTD and FDE.

The `backsub` function computes the solution to the set of linear equations described by:
$$A * X = B$$

The 1st argument to `backsub` is a struct converted from the result of `factor(A)`. The second argument to `backsub` is the matrix B. The matrix B can contain multiple right hand sides.

`backsub` returns a matrix X which contains the solution(s) to the aforementioned equations.

`backsub` utilizes the LAPACK subroutines DGETRS or ZGETRS if the input struct contains LU factors or LAPACK subroutins DSYTRS or ZHETRS if input struct contains the LDL factors.

**Syntax**
|Code| Function|
|:---|:---|
|`out = backsub( A_F, B );`|Returns the solution of $Ax = B$ by backsubstitution. The input *A_F* is a struct converted from the output of `factor(A)`. If A is a general matrix, the input struct must have three fields named "lu", "pvt", and "rcond". The value of fields "lu", "pvt", and "rcond" can be generated by `factor` function. If A is a symmetric matrix, the input struct must have three fields named "ldl", "pvt", and "rcond". The value of fields "ldl", "pvt", and "rcond" can be generated by `factor` function.|


**Example**
- A is a general matrix.

```msf
A = [1, 2, 3; 4, 5, 6; 7, 8, 0];
B = [1; 2; 3];

[Lu, Pvt, Rcond] = factor(A);
F = struct('lu': Lu, 'pvt': Pvt, 'rcond': Rcond);
X = backsub(F, B)

# verify the matrix X is the solution of matrix equation A * X = B
D = A * X - B

```
Result:
```msf
X =
  -0.333333333
   0.666666667
             0
D =
-1.11022302e-16
             0
             0
```


- A is a symmetric matrix

```msf
A = [1, 2, 0; 2, 5, 6; 0, 6, 9]
B = [5; 30; 39];

[Ldl, Pvt, Rcond] = factor(A);
F = struct("ldl": Ldl, "pvt": Pvt, "rcond": Rcond);
X = backsub(F, B)

# verify the matrix X is the solution of matrix equation A * X = B
D = A * X - B
```
Result:

```
X =
             1
             2
             3
D =
             0
             0
             0
```


**See also**
factor, inv, lu, solve



## ode
**Description**
Integrates Ordinary Differential Equations.
Used in FDTD and FDE.

`ode` integrates a system of N first order ordinary differential equations of the form:
$$dy(i)/dt = f(t, y(1), y(2), ..., y(N))$$

y(i) given at t.
        
The arguments to `ode` are:

- rhsf
A function that evaluates dy(i)/dt at t. The function takes two arguments and returns dy/dt. An example that generates dy/dt for Van der Pol's equation is shown below.
```msf
function xp = vdpol(t, x)
    xp = zeros(2, 1);
    xp(1) = x(1) * (1 - x(2)^2) - x(2);
    xp(2) = x(1);
end;
```

- ystart
The initial values of y, y(tstart).

- tstart
The initial value of the independent variable.

- tend
The final value of the independent variable.

- dtout
The output interval. The vector y will be saved at tstart, increments of tstart + dtout, and tend. If dtout is not specified, then the default is to store output at 101 values of the independent variable.

- relerr
The relative error tolerance. Default value is 1e-6.

- abserr
The absolute error tolerance. At each step, `ode` requires that:
$$abs(local error) <= abs(y)*relerr + abserr$$

For each component of the local error and solution vectors. The default value is 1e-6.

- uout
Optional. A user-supplied function that computes an arbitrary output during the integration. The *uout* must return a row-matrix at each dtout during the integration. It is entirely up to the user what to put in the matrix. The matrix is used to build up a larger matrix of the output, with one row for each dtout. The resulting matrix is returned by `ode` when the integration is complete.

The Fortran source code for `ode` is completely explained and documented in the text, 'Computer Solution of Ordinary Differential Equations: The Initial Value Problem' by L. F. Shampine and M. K. Gordon.



**Syntax**
|Code| Function|
|:---|:---|
|`out = ode( rhsf, tstart, tend, ystart, dtout, relerr, abserr, uout );`|Integrates a system of N first order ordinary differential equations.|

**See also**
backsub, filter



