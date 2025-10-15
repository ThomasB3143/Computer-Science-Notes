Section: [[Fundamentals of Linear Algebra (Root)]]
## Vector spaces

These are a [[Mathematical Structures|mathematical structure]] with two sets: scalars $F$ and vectors $V$. $F$ forms a [[Mathematical Structures#Fields|field]] whilst $V$ forms a commutative [[Mathematical Structures#Groups|group]] under addition ($u+v=v+u$). Scalar multiplication can map a scalar and a vector to a vector. Here are some important axioms:

- $1v-v$
- $a(u+v)=au+av$
- $(a+b)v=av+bv$
## An Example

A very common vector space is $\mathbb{R}^3$ over $\mathbb{R}$, which means a set of three dimensional real-numbered vectors and a set of real scalars. This is because $\mathbb{R}$ with addition and multiplication form a field whilst $\mathbb{R}^3$ forms a commutative group under addition. You can also multiply vectors by scalars, like so:

$\begin{pmatrix}1\\3\\2\end{pmatrix}*2=\begin{pmatrix}2\\6\\4\end{pmatrix}$
## Linear Combinations

Given a set of vectors $v_1,\dots,v_n$ and scalars $a_1,\dots,a_n$ we can form a linear combination $a_1v_1+\dots+a_nv_n$
### Spanning sets

The set of all possible linear combinations of a set of vectors is called a **span**. And a set of vectors $S$ is a **spanning set** for a vector space $(F,V)$ if $span(S)=V$ 
### Linear Independence

A set of vectors is **linearly dependent** if there exists a linear combination of $0$, where none of the scalars themselves are $0$. This also means that at least one vector can be written as a linear combination of the others

A set of vectors is **linearly independent** if there does not exist a linear combination of $0$, where none of the scalars themselves are $0$
###  Basis

A **basis** of a vector space is a set of vectors that [[Vector Spaces and Linear Combinations#Spanning sets|spans]] a vector space and is [[Vector Spaces and Linear Combinations#Linear Independence|linearly independent]], and the **dimensionality** of a vector space is the size of its basis

Example - find a basis for $\mathbb{R}^3$ over $\mathbb{R}$ 

We can use the **unit vectors** $\begin{pmatrix}1\\0\\0\end{pmatrix}\begin{pmatrix}0\\1\\0\end{pmatrix}\begin{pmatrix}0\\0\\1\end{pmatrix}$ as we can see this will **span** $\mathbb{R}^3$ and is **linearly independent** since no given vector can be formed from a linear combination of other vectors