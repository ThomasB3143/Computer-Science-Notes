Section: [[Inner Product Spaces (Root)]]

Suppose you want the dependency between two parameters $x$ and $y$. You've performed some experiments and collected some datapoints $(x_1,y_1),(x_2,y_2),\dots,(x_n,y_n)$.

You're going to want to fit a curve $y=f(x)$ in the plane to represent a relationship between the two. The simpler the better, so try a straight line $y=a+bx$ first. You can write that straight line as a series of equations like so:

$a+bx_1=y_1$
$a+bx_2=y_2$
until you're at
$a+bx_n=y_n$

This is looking rather matrix-*ish* so we can represent this as:

$\begin{bmatrix}1&x_1\\\vdots&\vdots\\1&x_n\end{bmatrix}\begin{bmatrix}a\\b\end{bmatrix}=\begin{bmatrix}y_1\\\vdots\\y_n\end{bmatrix}$

If you were a data-collecting wizard like me this system would be consistent and have a perfect solution to $a$ and $b$, but this is rarely the case. Instead we want to find the least squares solution to our system. This gives us the **least squares straight line fit**
## Uniqueness of Least Squares Solutions

When does the normal system $A^TAx=A^Tb$ have a unique solution? First we need to know that $A$ has linearly independent columns if, and only if, $A^TA$ is invertible

When this is the case, we can say that:

$x=(A^TA)^{-1}A^Tb$ 

We got this by diving both sides of the normal system by the invertible $A^TA$

We now want to use [[QR Decomposition]] (we can do this because $A$ has linearly independent columns) by substituting $A=QR$ and simplifying a *lot* like this:

$x=(A^TA)^{-1}A^Tb=((QR)^T(QR))^{-1}(QR)^Tb$

$(QR)^T=R^TQ^T$ so:

$x=(R^TQ^TQR)^{-1}R^TQ^Tb$

since $Q$ has orthonormal columns we know $Q^TQ=I$, because any diagonal element will be the squared sum of its components and thus $1$. Whereas any non-diagonal component will be the squared sum of two orthonormal vectors and as such $0$. Using this we get:

$x=(R^TIR)^{-1}R^TQ^Tb$
$x=(R^TR)^{-1}R^TQ^Tb$

Recall that for matrices $A_1,A_2,\dots A_n,(A_1A_2\dots A_n)^{-1}=A_n^{-1}\dots A_2^{-1}A_1^{-1}$ so we can expand the inverse we got there:

$x=R^{-1}(R^T)^{-1}R^TQ^Tb$
$x=R^{-1}Q^Tb$
## Projection Matrices

We showed that for a column vector $b$, if $W$ is the column space of $A$ with least squares solution $x$ to $Ax=b$, then $proj_Wb=Ax$

Remembering the **normal system** we can substitute $proj_Wb=Ax=A(A^TA)^{-1}A^Tb$

$P=A(A^TA)^{-1}A^T$ is called the **projection matrix**, and for any column vector $b$, the vector $Pb$ is the **orthogonal projection** of $b$ onto the column space of $A$

We like to use these in machine learning and data science to map vectors from a high-dimensional space to a smaller-dimensional space (next year?)

Example - given the following table, fit the data to a quadratic curve

|  x  |  y  | weight |
| :-: | :-: | :----: |
|  1  | -1  |   4    |
|  2  |  2  |   4    |
|  0  | -6  |   3    |
|  3  |  6  |   3    |
|  1  |  0  |   1    |
|  2  |  3  |   1    |
So we're looking for a curve in the form $y=a+bx+cx^2$, we want the least squares solution to the following system:

$Ax=y$  which turns out to be  $\begin{bmatrix}1&1&1\\1&2&4\\1&0&0\\1&3&9\\1&1&1\\1&2&4\end{bmatrix}\begin{bmatrix}a\\b\\c\end{bmatrix}=\begin{bmatrix}-1\\2\\-6\\6\\0\\3\end{bmatrix}$
We'll start by performing [[Gram-Schmidt Orthogonalisation]] on the columns of $A$ (REMEMBER WE ARE USING A [[Introduction to Inner Product Spaces#Weighted Euclidian Inner Product|WEIGHTED INNER PRODUCT]]) 

There is no way I'm going through all of that so doing all of that we get:

$q_1=\frac14(1,1,1,1,1,1)$
$q_2=\frac18(-1,1,-3,3,-1,1)$
$q_3=\frac{1}{4\sqrt{15}}(-3,-3,5,5,-3,-3)$

Stick it in a matrix and you get:

$QR=\begin{bmatrix}\frac14&\frac{-1}{8}&\frac{-3}{4\sqrt{15}}\\\frac14&\frac18&\frac{-3}{4\sqrt{15}}\\\frac14&\frac{-3}{8}&\frac{5}{4\sqrt{15}}\\\frac14&\frac38&\frac{5}{4\sqrt{15}}\\\frac14&\frac{-1}{8}&\frac{-3}{4\sqrt{15}}\\\frac14&\frac18&\frac{-3}{4\sqrt{15}}\end{bmatrix}\begin{bmatrix}4&6&13\\0&4&12\\0&0&\sqrt{15}\end{bmatrix}$

Invert $R$ and transpose $Q$ and multiply it by $y$ to get $x$ to get:

$x=R^{-1}Q^Ty=\frac{1}{160}\begin{bmatrix}-315\\306\\-32\end{bmatrix}\approx\begin{bmatrix}1.97\\1.91\\-0.2\end{bmatrix}$  



