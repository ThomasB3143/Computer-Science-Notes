Section: [[Fundamentals of Linear Algebra (Root)]]

In $n$ variables $x_1,\dots,x_n$ , a **linear equation** is one in the form:

$a_1x_1+a_2x_2+\dots+a_nx_n=b$ where all $a_i$ and $b$ are constants

Make a finite set of these and you have a **system of linear equations** (the title of this section!!). A system written as:

$\begin{matrix}a_{11}x_1+a_{12}x_2+\dots+a_{1n}x_n=b_1\\a_{21}x_1+a_{22}x_2+\dots+a_{2n}x_n=b_2\\\vdots\\a_{m1}x_1+a_{m2}x_2+\dots+a_{mn}x_n=b_m\end{matrix}$ 

Or represented as an equation involving matrices in the form $Ax=b$. Given that there are $m$ equations and $n$ variables:

- $A$ is a $m\times n$ matrix where the element $a_{ij}$ represents the coefficient of $x_i$ in equation $j$
- $x$ is an $n$ dimensional vector containing each variable in the system
- $b$ is an $m$ dimensional vector where each element represents the sum of coefficients (determined by the same row in $A$) for a given equation

To aid in solving a system, we can form an **augmented matrix** of the system $(A|b)$ like this:

$\begin{pmatrix}a_{11}&a_{12}&\dots&a_{1n}&b_1\\a_{21}&a_{22}&\dots&a_{2n}&b_2\\ all&the& way&down&to\\a_{m1}&a_{m2}&\dots&a_{mn}&b_m\end{pmatrix}$

A **solution** to a system is a sequence of numbers such that their assignment to each $x_i$ satisfies **all** equations. A **consistent** linear system has at least one solution
## Solutions

The linear system $\begin{matrix}x-y=1\\2x+y=6\end{matrix}$ has exactly **one** solution being $x=\frac73$ and $y=\frac43$

The linear system $\begin{matrix}x+y=4\\3x+3y=6\end{matrix}$ has **no** solutions  (we dub these **inconsistent**)

The linear system $\begin{matrix}x-y=1\\2x+2y=2\end{matrix}$ has **infinitely many** solutions, the solution set is all pairs of $x$ and $y$ in the form $x=1+y$ 
## Gaussian Elimination

Gauss elimination is applied to an augmented matrix of a linear system like shown earlier. The idea is to perform the **elementary row operations**:

- Multiply a row by a non-zero constant
- Interchange two rows
- Add a multiple of one row to another
### Row Echelon Form

A matrix in row echelon form has the following properties:

- If a row is not all zeroes then the first non-zero number is $1$
- Any all-zero rows are grouped together at the bottom
- If two successive rows are not all zeroes, the leading $1$ of the higher row must be in a column further to the left than that of the lower leading 1

Here is a great example displaying each requirement:

$\begin{pmatrix}1&4&-5&0&3\\0&0&1&2&0\\0&0& 0&1&2\\0&0&0&0&0\end{pmatrix}$ 
### Reduced Row Echelon form

Building on [[Systems of Linear Equations#Row Echelon Form|row echelon form]], **reduced row echelon form** has one more requirement. That each column with a leading $1$ has zeroes everywhere else, like this one:

$\begin{pmatrix}1&-1&0&2&2\\0&0&1&-1&5\\0&0& 0&0&0\\0&0&0&0&0\end{pmatrix}$ 

Once we have transformed an augmented matrix of a linear system to (r)ref, we can extract some solutions. But we have the following possibilities linking back to our [[Systems of Linear Equations#Solutions|possible solutions]]:

- Some row has a leading 1 in the last column. This is saying that $0x_1+\dots+0x_n=1$ thus saying the system has no solutions
- The number of leading 1s is equal to the number of variables. In this case the system has a unique solution
- The number of leading 1s is smaller than the number of variables (and no leading 1 in the last column). This means the system has Infinitely many solutions

Consider our previous example, this corresponds to the following set of equations:

$\begin{matrix}x_1&-x_2&&+2x_4&=2\\&&x_3&-x_4&=5\end{matrix}$

The variables corresponding to the leading 1s ($x_1$ and $x_3$ here) are the **leading variables**. The others are **free variables**

The **general solution** is a set of equations where the leading variables are expressed via free variables. Applying this to our previous example we get:

$x_1=x_2-2x_4+2$
$x_3=x_4+4$
### Algorithmic Steps to Gauss Elimination

To transform a matrix into [[Systems of Linear Equations#Row Echelon Form|row echelon form]] we follow this algorithm:

1. Identify the **pivot column**, this is the leftmost column with a non-zero$$\begin{pmatrix}0&0&-2&0&7&12\\2&4&-10&6&12&28\\2&4& -5&6&-5&-1\end{pmatrix}$$
2. Choose a **pivot**, a non-zero element in the pivot column and interchange the first row with another row to move the pivot to the top in this column (if necessary)$$\begin{pmatrix}2&4&-10&6&12&28\\0&0&-2&0&7&12\\2&4& -5&6&-5&-1\end{pmatrix}$$
3. Where $a$ is the pivot, multiply the first row by $a^{-1}$, this forms a leading 1$$\begin{pmatrix}1&2&-5&3&6&14\\0&0&-2&0&7&12\\2&4& -5&6&-5&-1\end{pmatrix}$$
4. Add suitable multiples of the first row to the rows below such that all numbers below the leading 1 are zeroes$$\begin{pmatrix}1&2&-5&3&6&14\\0&0&-2&0&7&12\\0&0&5&0&-17&-29\end{pmatrix}$$
5. Separate the top row from the rest and repeat steps 1-5 if there are non-zero rows remaining$$\begin{pmatrix}1&2&-5&3&6&14\\\hline 0&0&-2&0&7&12\\0&0&5&0&-17&-29\end{pmatrix}$$
For the example we were following, we end up with$$\begin{pmatrix}1&2&-5&3&6&14\\0&0&1&0&\frac{-7}{2}&-6\\0&0&0&0&1&2\end{pmatrix}$$
### Gauss-Jordan Elimination

To reduce the matrix further into [[Systems of Linear Equations#Reduced Row Echelon form|rref]] we need one more step on top of Gaussian elimination, lets follow on from our example

6. Beginning from the last non-zero row and working upward, add suitable multiples of each row to create zeroes above the leading 1s like so:

$\begin{pmatrix}1&2&-5&3&6&14\\0&0&1&0&0&1\\0&0&0&0&1&2\end{pmatrix}$ added $\frac72$ of the 3rd row to the 2nd row

This leaves us with a matrix in rref like this:

$\begin{pmatrix}1&2&0&3&0&7\\0&0&1&0&0&1\\0&0&0&0&1&2\end{pmatrix}$

From this we can form the system of equations represented by the matrix:

$\begin{matrix}x_1&+2x_2&&+3x_4&&=7\\&&x_3&&&=1\\&&&&x_5&=2\end{matrix}$

$x_2$ and $x_4$ are our **free variables**, with the others being our **leading variables**, so we shuffle our equations to get our **general solution**:

$x_1=7-2x_2-3x_4$
$x_3=1$
$x_5=2$
## Homogeneous Linear Systems

A linear system is **homogeneous** if $b$ is all zeroes. Such a system has a **trivial solution** where $x$ is all zeroes also, but potentially some **non-trivial solutions**

If a homogeneous linear system has $n$ free variables and the [[Systems of Linear Equations#Reduced Row Echelon form|rref]] of its augmented matrix has $r$ non-zero rows then the system has $n-r$ free variables. This means that a homogeneous linear system with more variables than equations has **infinitely many** solutions