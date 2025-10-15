Section: [[Fundamentals of Linear Algebra (Root)]] 
# Inverse

The **inverse** of a function $f$ undoes the operation $f$ and is written as $f^{-1}$. It must be **unique** for $f^{-1}$ to be a function otherwise it is a relation.

In the proper notation, where $f:X\rightarrow Y$ and $\forall x\in X,g(fx))=x$ and $\forall y\in Y,f(g(x))=y$
## Inverse of a $2\times2$ Matrix

Suppose we want the inverse of $\begin{pmatrix}1&2\\3&4\end{pmatrix}$, then we want:

$\begin{pmatrix}w&x\\y&z\end{pmatrix}\begin{pmatrix}1&2\\3&4\end{pmatrix}=\begin{pmatrix}1&0\\0&1\end{pmatrix}$

Since the multiplication of a matrix and its inverse produces the [[Linear Maps#Identity matrix|identity matrix]] 

Which (using [[Linear Maps#Matrix multiplication|matrix multiplication]]) gives us the equations:

$w+3x=1$
$2w+4x=0$
$y+3z=0$
$2y+4z=1$

Which gives us $\begin{pmatrix}-2&1\\\frac32&-\frac12\end{pmatrix}$

But we have a cool shortcut for the inverse of a $2\times2$ matrix:

$A^{-1}=\frac{1}{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$
## Inverse Commutes

If $AB=I$ then $A=IA=(AB)A=A(BA)$ so $BA=I$, hence $AA^{-1}=A^{-1}A=I$
## Inverse by Gauss-Jordan

Recall [[Systems of Linear Equations#Algorithmic Steps to Gauss Elimination|Gauss-Jordan elimination]]

Given $A$ we want to find $B$ such that $BA=AB=I$. We can use Gauss-Jordan elimination on the augmented matrix $A|I$

Example - find the inverse of $\begin{pmatrix}1&2\\3&4\end{pmatrix}$

$A|I=\begin{pmatrix}1&2&1&0\\3&4&0&1\end{pmatrix}$

Using elementary row operations, we want the $A$ portion of the augmented matrix to be $I$ like this:

$\begin{pmatrix}1&0&-2&1\\0&1&0&1\end{pmatrix}$

This gives us the matrix $(I|A^{-1})$

If the matrix cannot be converted to this form then the matrix cannot be inverted
## Rank

Remember that all vectors can be represented as a [[Vector Spaces and Linear Combinations#Linear Combinations|linear combination]] of basis vectors and under a [[Linear Maps|linear map]], $f:X\rightarrow Y,f(ax+by)=af(x)+bf(y)$

$f(X)$ is the [[Vector Spaces and Linear Combinations#Spanning sets|span]] of the column, called the **column space**, and the column **rank** is the dimension of the column space. Coincidentally this is equal to the number of linearly independent columns

Row space is the **span** of all row vectors, and row rank is the dimension of the row space. Similar to column rank, row rank is equal to the number of linearly independent rows

But what if I told you row rank and column rank were the *same?!?!?!* We know this because each step of Gauss-Jordan elimination leaves the row/column rank unchanged, and this can be done until we arrive at the identity matrix surrounded by zeroes. At this point, row rank is equal to the column rank.

Since they are the same, we can simply refer to the **rank** of a matrix, which is equal to the dimension of $f(X)$ 
### Getting the Rank

To get the rank of a matrix, we perform gaussian elimination and count the non-zero rows once in [[Systems of Linear Equations#Row Echelon Form|ref]]. A matrix has **full rank** if the rank is as high as possible (the maximum rank is equal to the greatest of the number of rows and the number of columns)
## Kernel

Where $f:X\rightarrow Y$ is a linear map, the **kernel** (or **null space**) of $f$ is the set of vectors that map to $0$. As luck would have it, the kernel forms a [[Vector Spaces and Linear Combinations#Vector spaces|vector space]], since all linear combinations of kernel elements are in the kernel
## Inverting Non-Square Matrices

Consider the linear map $f:X\rightarrow Y$

If $dim(X)<dim(Y)$ then (since $dim(f(X))\leq dim(X)$ ) we know that $dim(f(X)) < dim(Y)$. This means that some elements of $Y$ are not in $f(X)$ and therefore there exists **no** **inverse**

If $dim(X)>dim(Y)$ then the columns of the matrix are not linearly independent. This means that there are non-zero vectors that map to zero. So an inverse cannot be unique because $f(x+k)=f(x)$ where $k$ is in the [[Inverse, Rank and Kernel#Kernel|kernel]]. Therefore **no inverse**