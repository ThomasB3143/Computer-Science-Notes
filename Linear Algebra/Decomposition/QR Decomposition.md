Section: [[Decomposition (Root)]]

Let $A$ be an $m\times n$ matrix with linearly independent columns $u_1,\dots,u_n$. We can apply [[Gram-Schmidt Orthogonalisation]] to this set of columns to form $q_1,\dots,q_n$.

So how can we relate $A=[u_1|\dots|u_n]$ and $Q=[q_1|\dots|q_n]$? 

Well $\{q_1,\dots,q_n\}$ is an [[Gram-Schmidt Orthogonalisation#Orthogonal and Orthonormal Sets|orthonormal basis]] for $span(u_1,\dots,u_n)$ so we have

$u_1=\langle u_1,q_1\rangle q_1+\dots+\langle u_1,q_n\rangle q_n$ 
$u_2=\langle u_2,q_1\rangle q_1+\dots+\langle u_2,q_n\rangle q_n$
all the way down to...
$u_n=\langle u_n,q_1\rangle q_1+\dots+\langle u_n,q_n\rangle q_n$

This is looking suspiciously matrix-ey

$A=[u_1|\dots|u_n]=[q_1|\dots|q_n]\begin{bmatrix}\langle u_1,q_1\rangle&\langle u_2,q_1\rangle&\cdots&\langle u_n,q_1\rangle\\\langle u_1,q_2\rangle&\langle u_2,q_2\rangle&\cdots&\langle u_n,q_2\rangle\\ \text{all} & \text{the} & \text{way} & \text{down} \\\langle u_1,q_n\rangle&\langle u_2,q_n\rangle&\cdots&\langle u_n,q_n\rangle\end{bmatrix}=QR$

But we know that for all $j\geq2,q_j$ is orthogonal to $u_1,\dots,u_{j-1}$, hence $R$ is **upper triangular** like this:

$\begin{bmatrix}\langle u_1,q_1\rangle&\langle u_2,q_1\rangle&\cdots&\langle u_n,q_1\rangle\\0&\langle u_2,q_2\rangle&\cdots&\langle u_n,q_2\rangle\\ \text{all} & \text{the} & \text{way} & \text{down} \\0&0&\cdots&\langle u_n,q_n\rangle\end{bmatrix}$
## Least Squares

Recall that the **column space** is the span of the column vectors in a matrix

Now assume we have an [[Systems of Linear Equations#Solutions|inconsistent system of linear equations]] $Ax=b$. Can we find a vector that comes as close as possible to being a solution? This question defines the **Least Squares Problem** as such:

Given a linear system $Ax=b$ with $m$ equations and $n$ variables, find a vector $x$ that minimises $||b-Ax||$ (the [[Norms and Dot Product#Euclidian Norm|Euclidian inner product]])

$x$ is the **least squares solution** and $||b-Ax||$ is the **least squares error**

If we trust equations differently, we can represent this using the [[Introduction to Inner Product Spaces#Weighted Euclidian Inner Product|weighted Euclidian inner product]] 
## Best Approximation Theorem

If $W$ is a finite-dimensional subspace in an inner product space $V$ and $b\in V$, then $proj_Wb$ is the best approximation to $b$ from $W$ in the sense that $||b-proj_Wb||\leq||b-w||$ for each vector $w\in W,w\neq proj_Wb$ 
## Finding the Solution

Let $W=\{Ax|x\in\mathbb{R}^n\}$ be the column space of $A$ (its the span of the columns because its all linear combinations of the columns)

Since $proj_Wb$ is the best approximation from $b$ to $W$, least square solutions to $Ax=b$ are exact solutions to $Ax=proj_Wb$

We can compute $proj_Wb$ and solve the system, but there is a cooler and more useful way

The representation $b=w_1+w_2,w_1\in W,w_2\in W^\bot$ is unique so $Ax=proj_Wb$ is equivalent to $b-Ax\in W^\bot$ 

The columns of $A$ are the rows of $A^T$, so the condition $b-Ax\in W^\bot$ is equivalent to $A^T(b-Ax)=0$ and so...

$A^TAx=A^Tb$ (this is the **normal equation** associated with $Ax=b$)

Example - Using the Euclidian dot product, find least square solutions for the linear system:

$x_1-x_2=4$
$3x_1+2x_2=1$
$-2x_1+4x_2=3$

Lets start by defining our $A$, $x$ and $b$ like so:

$A=\begin{bmatrix}1&-1\\3&2\\-2&4\end{bmatrix},x=\begin{bmatrix}x_1\\x_2\end{bmatrix},b=\begin{bmatrix}4\\1\\3\end{bmatrix}$

$A^TAx=A^Tb$ so we get:

$\begin{bmatrix}1&3&-2\\-1&2&4\end{bmatrix}\begin{bmatrix}1&-1\\3&2\\-2&4\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}=\begin{bmatrix}1&3&-2\\-1&2&4\end{bmatrix}\begin{bmatrix}4\\1\\3\end{bmatrix}$

Compute those matrix products to get our brand new *consistent* system of equations:

$\begin{bmatrix}14&-3\\-3&21\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}=\begin{bmatrix}1\\10\end{bmatrix}$ 

Solving this yields $x_1=\frac{17}{95}$ and $x_2=\frac{143}{285}$ and we can easily compute the error vector and error using the equations from the [[QR Decomposition#Least Squares|start]]


