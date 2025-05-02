Section: [[Fundamentals of Linear Algebra (Root)]]

The determinant of a matrix (only **square** matrices allowed) is the signed image of the unit square, written as $det(A)$ or $|A|$. For a $2\times2$ matrix:

$det\left(\begin{pmatrix}a&b\\c&d\end{pmatrix}\right)=ad-bc$

Note that the determinant is $0$ when the columns are [[Vector Spaces and Linear Combinations#Linear Independence|linearly dependent]] (this will be very important much later)
## Properties of the determinant

For these we will be defining the determinant as a function on the **columns** of a matrix
### Linearity

$det(ac_1,\dots,c_n)=a*det(c_1,\dots,c_n)$ and $det(c_1+c_1^\prime,\dots,c_n)=det(c_1,\dots,c_n)+det(c_1^\prime,\dots,c_n)$

We can explain this as multiplying one of the vectors by a scalar will multiply the volume of the unit square by that scalar
### Alternating

If any two columns are equal, the determinant is $0$

This is because if the image of two vectors is the same then the image space has collapsed
### Identity

The determinant of the identity matrix is $1$, because the unit square/cube/hypercube has area/volume/whatever 1
## Diagonal Matrices

The determinant of a diagonal matrix is the product of all diagonal elements
## Laplace Expansion

$det(c)=\sum\limits^n_{j=1}(-1)^{i+j}c_{ij}M_{ij}$

Where $M_{ij}$ is the **minor**, the determinant of the matrix $C$ with row and column $i$ and $j$ removed. So this expansion is **recursive** in its definition.

Here is a handy visual to know if $(-1)^{i+j}=-1$ or $+1$ :

$\begin{pmatrix}+&-&+&-\\-&+&-&+\\+&-&+&-\\-&+&-&+\end{pmatrix}$ this pattern continues for matrices of a higher dimension

Example - find the determinant of the following matrix:

$A=\begin{pmatrix}1&2&3\\3&1&2\\0&0&1\end{pmatrix}$
$det(A)=1det\left(\begin{pmatrix}1&2\\0&1\end{pmatrix}\right)-2det\left(\begin{pmatrix}3&2\\0&1\end{pmatrix}\right)+3det\left(\begin{pmatrix}3&1\\0&0\end{pmatrix}\right)$ 
$det(A)=1*(1*1+2*0)-2(3*1+2*0)+3(3*0+1*0)$
$det(A)=1*1-2*3+3*0$
$det(A)=-5$
## Combining matrices

$det(AB)=det(A)det(B)$

$det(A^{-1})=\frac{1}{det(A)}$ hence a determinant of $0$ implies **no inverse**
## Uses of Determinants

- Finding the area/volume of images
- Determining whether a set of vectors is [[Vector Spaces and Linear Combinations#Linear Independence|linearly dependent]]
- Finding out if a matrix has an inverse
- Finding the inverse of a matrix
- Solving equations with matrices