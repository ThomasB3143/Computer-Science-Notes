Section: [[Decomposition (Root)]]

Recall the definition of both [[All About Eigens#Eigenvalues and Eigenvectors|eigenvectors and eigenvalues]]

Eigendecomposition is when we decompose a matrix $A$ into $PDP^{-1}$ where $P$ is a matrix of eigenvectors and $D$ is a diagonal matrix of eigenvalues.

This decomposition is especially useful for self-matrix multiplication as $A^k=PD^kP^{-1}$
# Uses of Eigendecomposition

## Raising to Powers

Suppose you have a matrix $A$ and you want to find $A^{100}$. Normally this would take forever, but we can **decompose** $A$ into $PDP^{-1}$ and try raising it to the power like so:

$(PDP^{-1})^{100}=(PDP^{-1})(PDP^{-1})\dots=PDP^{-1}PDP^{-1}\dots=PDDP^{-1}\dots=PD^{100}P^{-1}$

All $P$ and $P^{-1}$ except those on either ends of the product cancel out! This means we only need to raise $D$ to a power, which is much easier. $D$ is **diagonal**, so we can simply raise each element to the power of $100$ to find $D^{100}$
# Similarity

Two matrices $A$ and $B$ are **similar** if $A=P^{-1}BP$ for some invertible $P$

If two matrices are similar they have equal [[Determinants|determinants]]

If, **and only if**, two matrices are similar they represent the same linear operator, potentially in different bases. That makes no sense without the following information:

- Let $T:\mathbb{R}^n\rightarrow\mathbb{R}^n$ be a linear operator and $S=\{v_1,\dots,v_n\}$ be a basis in $\mathbb{R}^n$
- Let $[T]_s$ be the $n\times n$ matrix whose columns are the vectors $T(v_i)$ in basis $S$. This is called the **matrix of $T$ in $S$**
- You can also say that it represents $T$ in basis $S$
- If $S$ is the standard basis then $[T]_s$ is the standard matrix of $T$

So basically what we were saying earlier is that $A$ and $B$ are similar if there is a linear operator $T$ and two bases $S,S^\prime$ such that $A=[T]_s$ and $B=[T]_{s^\prime}$
# Diagonalisation

A matrix is **diagonalisable** if it is [[Eigendecomposition#Similarity|similar]] to a diagonal matrix, hence there exists an invertible matrix $P$ such that $P^{-1}AP$ is diagonal. $P$ is said to **diagonalise** $A$

If $A$ is diagonalisable then it decomposes as $A=PDP^{-1}$

An $n\times n$ matrix is diagonalisable if, **and only if**, it has $n$ [[Vector Spaces and Linear Combinations#Linear Independence|linearly independent]]  eigenvectors. We can prove the $\implies$ then the $\impliedby$ like so, starting with $\implies$:

- assume there is an invertible matrix $P$ and a diagonal matrix of eigenvalues $D$ such that $D=P^{-1}AP$ or $AP=PD$
- Denoting the columns of $P$ by $p_1,\dots,p_n$ we can see that $AP=[Ap_1|\dots|Ap_n]$
- $PD=[\lambda_1p_1|\dots|\lambda_np_n]$
- Since $AP=PD$ we can say $Ap_i=\lambda_ip_i$
- $P$ is invertible, and thus its rank is $n$ and vectors $p_1,\dots,p_n$ are linearly independent
- So none of them are $0$, so each of them is an eigenvector

Now for $\impliedby$:

- Assume that $A$ has $n$ linearly independent eigenvectors $p_1,\dots,p_n$ and let $\lambda_1,\dots,\lambda_n$ be the corresponding eigenvalues
- $P=[p_1|\dots|p_n]$ and $D=diag(\lambda_1,\dots,\lambda_n)$
- $AP=PD$
- The columns of $P$ are linearly independent, so its rank is $n$ and it is invertible
- $AP=PD$ is equivalent to $D=P^{-1}AP$ , hence $A$ must be diagonalisable
# An Algorithm to Diagonalise

For a matrix $A$

1. Solve the [[All About Eigens#Eigenvalues and Eigenvectors|characteristic equation]] to find the eigenvalues of $A$
2. Find a basis in each eigenspace of $A$ and merge the bases into a set $S$
3. If $S$ has fewer than $n$ vectors then $A$ is not diagonalisable
4. Form the matrix $P=[p_1|\dots|p_n]$ where $S=\{p_1,\dots,p_n\}$
	1. The set $S$ contains $n$ vectors and is linearly independent (proved)
	2. So $S$ is a basis for $\mathbb{R}^n$ and $P$ is invertible
5. The matrix $D=P^{-1}AP$ is diagonal, $D=diag(\lambda_1,\dots,\lambda_n)$ 

Example - diagonalise the following matrix:

$A=\begin{pmatrix}0&0&-2\\1&2&1\\1&0&3\end{pmatrix}$

First we need to find the eigenvalues by first finding the characteristic equation using $\det(\lambda I-A)$ like so:

$\det(\lambda I-A)=\det\begin{pmatrix}\lambda &0&2\\-1&\lambda-2&-1\\-1&0&\lambda-3\end{pmatrix}$

$=(\lambda-2)(\lambda(\lambda-3)+2)=(\lambda-2)(\lambda^2-3\lambda+2)$
$=(\lambda-2)(\lambda-2)(\lambda-1)$   
$\lambda_1=1$
$\lambda_2=2$

We find the basis of the eigenspace for $\lambda_1$ using $(\lambda I-A)x=0$ like this:

$(\lambda I-A)x=\begin{pmatrix}1&0&2\\-1&-1&-1\\-1&0&-2\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\end{pmatrix}=\begin{pmatrix}0\\0\\0\end{pmatrix}$

Solving the corresponding system of linear equations we get:

$x_1=-2t,x_2=x_3=t$

$\therefore x=t\begin{pmatrix}-2\\1\\1\end{pmatrix}$

Hence the basis is $\begin{pmatrix}-2\\1\\1\end{pmatrix}$
Now we do the same to find the eigenspace for $\lambda_2$ like so:

$(\lambda I-A)x=\begin{pmatrix}2&0&2\\-1&0&-1\\-1&0&-1\end{pmatrix}\begin{pmatrix}x_1\\x_2\\x_3\end{pmatrix}=\begin{pmatrix}0\\0\\0\end{pmatrix}$

Since this translates to the same equation $x_1=-x_3$ three times, we can assume $x_2$ to be anything. 

Hence the basis vectors here are $\begin{pmatrix}-1\\0\\1\end{pmatrix}$ and $\begin{pmatrix}0\\1\\0\end{pmatrix}$

Now with our eigenvectors we can represent $A$ as $P^{-1}DP$ like so:

$D=\begin{pmatrix}1&0&0\\0&2&0\\0&0&2\end{pmatrix}$ and $P=\begin{pmatrix}-2&-1&0\\1&0&1\\1&1&0\end{pmatrix}$

It is important to note that an Eigendecomposition is not **unique**, as you can easily swap the order of eigenvalues in $D$ and do the same for the corresponding eigenvectors in $P$