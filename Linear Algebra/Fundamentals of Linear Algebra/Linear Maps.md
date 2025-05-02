Section: [[Fundamentals of Linear Algebra (Root)]]
## Revisiting the Basis

To understand linear maps we first need to recall the definition of a [[Vector Spaces and Linear Combinations#Basis|basis]], and understand that the representation of any vector in a vector space as a linear combination of a given basis is **unique**. This is true because, were it not true, we could subtract the two representations which implies that the basis is not [[Vector Spaces and Linear Combinations#Linear Independence|linearly independent]] and thus not a basis (contradiction)

For most cases, when referring to the "basis" of $\mathbb{R}^n$ we will be using the **canonical basis** $\{e_1,\dots,e_n\}$ where $e_i$ is a vector with a $1$ in the $i^\text{th}$ position and $0$ elsewhere
## Linear Maps

If we have a function $f:V\rightarrow W$ where $V$ and $W$ are over a field $F$, then $f$ is a linear map if:

- $f(u+v)=f(u)+f(v)$
- $f(av)=af(v)$

Some very popular examples include scaling in $\mathbb{R}^3$, rotation and reflection

But how does this tie into basis vectors I hear you ask? Well every vector can be represented as a linear combination of basis vectors. Using the previous rules for a linear map we can characterise a linear map by how it acts upon the basis vectors that form a vector

The result of applying a linear map to a vector is its **image**

Example - rotate $v=(2,3)$ $90\degree$ anti-clockwise

First we need to consider the images of the **canonical basis vectors** $e_1(1,0)$ and $e_2(0,1)$ for the rotation $r$

$r(e_1)=(0,1)$ and $r(e_2)=(-1,0)$
$v=2e_1+3e_2$ 
$r(v)=r(2e_1)+r(3e_2)$
$r(v)=2r(e_1)+3r(e_2)$
$r(v)=2(0,1)+3(-1,0)$
$r(v)=(-3,2)$
## Representing as a Matrix

You can represent a linear map as a matrix by concatenating the images of basis vectors like so:

$A=\begin{pmatrix}a_{11}&a_{12}&\dots&a_{1n}\\a_{21}&a_{22}&\dots&a_{2n}\\\vdots&\vdots&\ddots&\vdots\\a_{m1}&a_{m2}&\dots&a_{mn}\end{pmatrix}$ 

Where $a_{ij}$ is the $i^\text{th}$ component of the image of the $j^\text{th}$ basis vector

It is also important to note that an $m\times n$ matrix maps a vector in $\mathbb{R}^n$ to one in $\mathbb{R}^m$
## Identity matrix

All basis vectors map to themselves via the identity matrix $I$

$I=\begin{pmatrix}1&0&\dots&0\\0&1&\dots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\dots&1\end{pmatrix}$ and $AI=A$ 
## Combining Linear maps

We can combine linear maps by multiplying the matrices they are represented by (with the order of execution from right to left)
## Matrix multiplication

Matrices can only be multiplied if the first one has the same number of columns as the second one has rows. So given matrices $A\in\mathbb{R}^{m\times n}$ and $B\in\mathbb{R}^{n\times k}$, the elements $c_{ij}$ of the product $C=AB\in\mathbb{R}^{m\times k}$ :

$c_{ij}=\sum\limits^n_{l=1}a_{il}b{lj}$

### Matrix Multiplication Example

$\begin{pmatrix}1&2&3\\3&2&1\end{pmatrix}\begin{pmatrix}0&2\\1&-1\\0&1\end{pmatrix}=\begin{pmatrix}1*0+2*1+3*0&1*2+2*-1+3*1\\3*0+2*1+1*0&3*2+2*-1+1*1\end{pmatrix}=\begin{pmatrix}2&3\\2&5\end{pmatrix}$
