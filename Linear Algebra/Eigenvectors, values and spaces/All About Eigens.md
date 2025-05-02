Section: [[Eigenvectors, values and spaces (Root)]]
# Eigenvalues and Eigenvectors

An **eigenvector** $x$ of $A$ is a non-zero vector such that for some scalar **eigenvalue** $\lambda$:

$Ax=\lambda x$

Example:

$\begin{bmatrix}3&0\\8&-1\end{bmatrix}$ has an eigenvector $\begin{bmatrix}1\\2\end{bmatrix}$ corresponding to eigenvalue $3$ because...

$\begin{bmatrix}3&0\\8&-1\end{bmatrix}\begin{bmatrix}1\\2\end{bmatrix}=\begin{bmatrix}3\\6\end{bmatrix}=3x$

Characteristic equation of a matrix: 

$det(\lambda I-A)=0$ 

we get this because $Ax=\lambda x \therefore Ax=\lambda Ix \therefore (\lambda I-A)x=0$ 
The last equation only has a solution $x\neq 0$ if $det(\lambda I-A)=0$ 

The characteristic equation can be simplified to a polynomial of order $n$ (where $n$ is the order of $A$), this is called the **characteristic polynomial** (denoted $p(\lambda)$ )

# Eigenspaces

Where $\lambda_0$ is an eigenvalue of $A$, the null space of $\lambda_0I-A$ is the **eigenspace** of $A$ corresponding to $\lambda_0$

The non-0 vectors in this space are eigenvectors corresponding to the eigenvalue

Example - Finding the eigenspace of $A=\begin{bmatrix}2&-1\\10&-9\end{bmatrix}$ corresponding to $\lambda=-8$ :

Form the equation $(-8I-A)x=0$ like so:

$\begin{bmatrix}-10&1\\-10&1\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}=\begin{bmatrix}0\\0\end{bmatrix}$ or $\begin{matrix}-10x_1+x_2=0\\-10x_1+x_2=0\end{matrix}$ therefore one basis is $\{(1,10)\}$  

**Algebraic multiplicity** of an eigenvalue $\lambda_0$ is the power to which $(\lambda-\lambda_0)$ appears as a factor of the characteristic polynomial. **Geometric multiplicity** is the dimension of an eigenvalue's eigenspace. For any given eigenvalue of a square matrix, the algebraic multiplicity is greater than or equal to the geometric multiplicity.

Example exam question: Where the characteristic polynomial of a matrix is $\lambda^3+a\lambda^2+b\lambda+1$ and the matrix has $i$ as an eigenvalue, find (or prove unfindable) the following:

1) The degree of the matrix

The characteristic polynomial has identical degree to the matrix, therefore 3

2) The eigenvalues of the matrix

If $i$ is an eigenvalue and the characteristic polynomial has real coefficients only, then $-i$ is also an eigenvalue. Now we can factorise the characteristic polynomial like so:

$\lambda^3+a\lambda^2+b\lambda+1=(\lambda+i)(\lambda-i)(\lambda+r)=(\lambda^2+1)(\lambda+r)=\lambda^3+r\lambda^2+\lambda+r$ 
$\therefore a=b=r=1$ and the eigenvalues are $\{i,-i,-1\}$

3) Is the matrix invertible?

the determinant is the product of the eigenvalues, $-i\times i\times -1=ii=-1\neq0$
$\therefore$ the matrix is invertible!







