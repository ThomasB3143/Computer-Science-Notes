Section: [[Eigenvectors, values and spaces (Root)]]

Consider the matrix $A=\begin{bmatrix}-2&-1\\5&2\end{bmatrix}$ 
$det(\lambda I-A)=\lambda^2+1=0$ 

This equation has no real roots, but we can still find complex eigenvalues

Complex numbers are in the form $z=a+bi$ where $a,b\in\mathbb{R}$ and $i=\sqrt{-1}$
$Re(z)=a$ and $Lm(z)=b$
$|z|=\sqrt{a^2+b^2}$ and this is the modulus
$\bar{z}=a-bi$ and this is the complex conjugate
You can view complex number as a vector in $\mathbb{R}^2$ if you really want, then addition and multiplication by a real number is the same in $\mathbb{C}$ and $\mathbb{R}^2$ 

Complex Conjugate Properties (for vectors $u,v\in\mathbb{C}^n$ and scalar $k\in\mathbb{C}$):
- $\bar{\bar{u}}=u$
- $\overline{ku}=\bar k\bar u$ 
- $\overline{u\pm x}=\overline{u}\pm\overline{v}$
For complex matrices $A$ and $B$:
- $\overline{\overline{A}}=A$
- $\overline{A^T}=\overline{A}^T$
- $\overline{AB}=\bar A\bar B$

Complex Dot Product - for complex vectors $u,v$ the complex dot product is:

$u\cdot v=u_1\bar v_1+\dots+u_n\bar v_n$

And the Euclidian norm is:

$||v|| = \sqrt{u\cdot v}=\sqrt{|v_1|^2+\dots+|v_n|^2}$

Complex dot products have the following properties:

- $u\cdot v=\overline{v\cdot u}$
- $u\cdot(v+w)=u\cdot v+u\cdot w$
- $(ku)\cdot v=k(u\cdot v)=u\cdot(kv)$

If $\lambda$ is an eigenvalue of a real, square matrix with an eigenvector $x$, then $\bar{\lambda}$ and $\bar x$ are an eigenvalue and corresponding eigenvector of the matrix

Proof: Since $A$ is real, $\bar A=A\therefore A\bar x=\bar A\bar x = \overline{Ax}=\overline{\lambda x}=\bar\lambda\bar x$

If a matrix is real and symmetric, then all eigenvalues are real