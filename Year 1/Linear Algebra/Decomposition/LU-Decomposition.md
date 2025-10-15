Section: [[Decomposition (Root)]] 

The LU decomposition of a square matrix $A$ is its factorisation into matrices $LU$, where $L$ and $U$ are **lower and upper triangular** respectively
## Usage in Solving Linear Systems

Consider the following system $Ax=b$, if we can break $A$ down into $LU$ then we can say that $LUx=b$

Now denote $Ux=y$ and substitute it in to get $Ly=b$

Solve this lovely triangular linear system for $y$

Now you can solve the once again lovely linear system $Ux=y$ for $x$

Example - solve the following linear system $Ax=b$

$\begin{bmatrix}2&6&2\\-3&-8&0\\4&9&2\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}2\\2\\3\end{bmatrix}$

Lets break down $A$ into $LU$ (we will show you how to do this later just trust me on this one)

$\begin{bmatrix}2&0&0\\-3&1&0\\4&-3&7\end{bmatrix}\begin{bmatrix}1&3&1\\0&1&3\\0&0&1\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}2\\2\\3\end{bmatrix}$

Do the first substitution and solve the following linear system of equations:

$\begin{bmatrix}2&0&0\\-3&1&0\\4&-3&7\end{bmatrix}\begin{bmatrix}y_1\\y_2\\y_3\end{bmatrix}=\begin{bmatrix}2\\2\\3\end{bmatrix}$ to get $\begin{bmatrix}y_1\\y_2\\y_3\end{bmatrix}=\begin{bmatrix}1\\5\\2\end{bmatrix}$

Great! Now do $Ux=y$ like this:

$\begin{bmatrix}1&3&1\\0&1&3\\0&0&1\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}1\\5\\2\end{bmatrix}$ to get $\begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix}=\begin{bmatrix}2\\-1\\2\end{bmatrix}$ 
## Conditions for Decomposition

Where $A$ is a square matrix and $U$ be its row echelon form, if **no row exchanges** were performed to get to $U$ then $A$ can be factorised as $A=LU$

This means that we never get a $0$ in a pivot position in the process of getting from $A$ to $U$
## The Process

1. Keep track of the row operations to get to $U$
2. Let $E_1,\dots,E_K$ be the corresponding elementary matrices in order of the aforementioned row 
3. Compute $L=E_1^{-1}\dots E_k^{-1}$ by applying the row operations to the identity matrix

Here is a simple example:

$A=\begin{bmatrix}2&-4\\3&-2\end{bmatrix}=\begin{bmatrix}2&0\\3&4\end{bmatrix}\begin{bmatrix}1&-2\\0&1\end{bmatrix}=LU$ 

To get from $A$ to $U$ we:

1. Divided the top row by 2
2. Subtracted 3 lots of the top row to the bottom row
3. Divided the bottom row by 4

So to get from $I$ to $L$ we:

1. Multiplied the bottom row by 4 (inverse of step 3)
2. Added 3 lots of the top row to the bottom row (inverse of step 2)
3. Multiplied the top row by 2 (inverse of step 1)

So you can see that the simpler way of doing all the inverse elementary matrix business is just by carrying out the inverse of each operation in **reverse** order to what you did to get $U$!
## Permutation Matrices

We mentioned before that the $LU$ method fails when row exchanges are needed. To solve this, we permute the rows in advance using a matrix $P$ that looks something like this:

$\begin{bmatrix}0&0&0&1\\0&1&0&0\\1&0&0&0\\0&0&1&0\end{bmatrix}$
## PLU-Decomposition

Like LU-decomposition, this represents $A$ as $PLU$. **EVERY** square matrix can be composed this way

$A=PLU$ is equivalent to $P^TA=LU$ since $P^{-1}=P^T$

We can still use this to solve linear equations like so:

1. $P^T$ is invertible, so $Ax=b$ has the same solutions as $P^TAx=P^Tb$
2. Compute $b^\prime=P^Tb$ and solve $LUx=b^\prime$
