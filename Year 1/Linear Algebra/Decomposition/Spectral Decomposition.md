Section: [[Decomposition (Root)]]
## Orthogonal Matrices

A square $Q$ is **orthogonal** if $Q^T=Q^{-1}$ or $Q^TQ=I$

The following statements are **equivalent**:

1. $Q$ is orthogonal, 𓆏 is a frog
2. The rows of $Q$ form an orthonormal basis in $\mathbb{R}^n$ (with Euclidian inner product)
3. So do the columns!
## Properties

1. The transpose of an orthogonal matrix is also orthogonal
2. The inverse is orthogonal too
3. The product of orthogonal matrices is orthogonal
4. The determinant is 1 or -1
## As a Linear Operator

If $Q$ is **orthogonal** then:

1. $||Qx||=||x||$
2. $\langle Qx,Qy\rangle=\langle x,y\rangle$
## Orthogonal Diagonalisation

Recall [[Eigendecomposition#Similarity|similarity]] and [[Eigendecomposition#Diagonalisation|diagonalisation]]

When we say $A$ and $B$ are similar if there is an invertible matrix $P$ such that $P^{-1}AP=B$, we can choose $P$ to be **orthogonal** and say that $A$ and $B$ are **orthogonally similar**

We'd also say that $A$ is **orthogonally diagonalisable**
## The Spectral Theorem

If $A$ is orthogonally diagonalisable then:

1. $A$ has an orthonormal set of $n$ eigenvectors
2. $A$ is symmetric
## Eigen-properties of Symmetric Matrices

If $A$ is symmetric then:

1. all eigenvalues of $A$ are real
2. Eigenvectors from different eigenspaces are **orthogonal**
## Orthogonally Diagonalising a Matrix

For our matrix $A$:

1. Find the eigenvalues and a basis in each eigenspace of $A$
2. Do some [[Gram-Schmidt Orthogonalisation]] to each basis to get an **orthonormal basis** for each eigenspace
3. Form the matrix $Q$ (we just found the columns in step 2). $Q$ will orthogonally diagonalise $A$ and the diagonal of $D=Q^TAQ$ contains the eigenvalues of $A$ in the same order as eigenvectors in $Q$

Steps 1 and 3 were already things you do for diagonalisation. Unlike that algorithm, this one ALWAYS works (as long as the matrix is symmetric)

Example - Orthogonally diagonalise the following matrix $A$

$A=\begin{bmatrix}4&2&2\\2&4&2\\2&2&4\end{bmatrix}$

We find the eigenvalues to be $\lambda_1=2,\lambda_2=8$

The bases for the eigenspaces are $\{(-1,1,0),(-1,0,1)\}$ under $\lambda_1$ and $\{(1,1,1)\}$ under $\lambda_2$

Gram-Schmidt them to get $\{(-1\sqrt2,1\sqrt2,0),(\frac{-1}{\sqrt6},\frac{-1}{\sqrt6},\frac{2}{\sqrt6})\}$ and $\{(\frac{1}{\sqrt3},\frac{1}{\sqrt3},\frac{1}{\sqrt3})\}$

Now $Q=\begin{bmatrix}-1\sqrt2&\frac{-1}{\sqrt6}&\frac{1}{\sqrt3}\\1\sqrt2&\frac{-1}{\sqrt6}&\frac{1}{\sqrt3}\\0&\frac{2}{\sqrt6}&\frac{1}{\sqrt3}\end{bmatrix}$ and $Q^TAQ=\begin{bmatrix}2&0&0\\0&2&0\\0&0&8\end{bmatrix}$
## Spectral Decomposition

This is basically decomposing $A$ into $QDQ^T$
