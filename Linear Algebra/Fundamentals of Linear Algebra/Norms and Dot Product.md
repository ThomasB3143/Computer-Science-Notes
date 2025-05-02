Section: [[Fundamentals of Linear Algebra (Root)]]
## Euclidian Norm

Basically the Pythagorean theorem applied to any dimension. So for $x=(x_1,x_2,\dots,x_n)\in\mathbb{R}^n$, the Euclidian norm is defined as:

$||x||_2=\sqrt{\sum\limits^n_{i=0}x_i^2}$

Since this is the default norm we shorten it to $||x||$
## Unit Vectors

A unit vector has a length/norm of 1, so any non-zero vector can be divided by its norm to define the unit vector in its direction like this:

$\hat{x}=\frac{1}{||x||_2}x$
## Generalised Norms

Given a vector space $X$ and a function $d:X\rightarrow\mathbb{R}$, it is a **norm** if it satisfies the following:

- **Triangle Inequality** - $d(x+y)\leq d(x)+d(y)$ for all $x,y\in X$
- **Absolute Homogeneity** - $d(sx)=|s|d(x)$ for all $x\in X$ and $s\in\mathbb{R}$
- **Positive Definite** - $d(x)=0\iff x=0$
## Manhattan Norm

This can be used to represent **Manhattan distance** (the distance between two points where you can only travel along one dimension at a time). This is defined as:

$\sum\limits^n_{i=0}|x_i|$
## P-Norms

We can define the p-norm $\ell_p$ on $\mathbb{R}^n$ as:

$||x||_p=\sqrt[p]{\sum\limits_{i=0}^n|x_i|^p}$ 

So $\ell_1$ is the [[Norms and Dot Product#Manhattan Norm|Manhattan norm]] whilst $\ell_2$ is the [[Norms and Dot Product#Euclidian Norm|Euclidian norm]]
## To the Limits

If $p\rightarrow\infty$ then larger terms will dominate, so $\ell_\infty$ is the largest absolute value of all components of a vector

If $p\rightarrow0$ and we assume $0^0$ to be $0$, we can define $\ell_0$ as the number of components not equal to $0$. This is called **Hamming distance** but **not** a norm as it violates the rules on [[Norms and Dot Product#Generalised Norms|absolute homogeneity]] (taking out a scalar will not multiply the norm by said scalar) 
## Dot Product

given vectors $a,b$ we can define:

$a\cdot b=||a||_2||b||_2\cos\theta=\sum\limits^n_{i=1}a_ib_i$

Where $\theta$ is the angle between $a$ and $b$
## Properties of Dot Product

- Finds projection of a vector in the direction of the other
- $\hat{a}\cdot\hat{b}=\hat{b}\cdot\hat{a}=\cos\theta$
- $(sa)\cdot b=s(a\cdot b)$
- $(a_1+a_2)\cdot b=a_1\cdot b+a_2\cdot b$
- $a\cdot b=0\iff$ they are **orthogonal** (perpendicular) or one is zero
- $a\cdot a=||a||^2_2$
## Orthonormality

- Vectors are **orthogonal/perpendicular** when their dot product is $0$
- Vectors are **normal** if their $\ell_2$ norm is $1$ (so they are unit vectors)
- A set of vectors is **orthonormal** if they are all orthogonal and normal
- We often want to have an orthonormal [[Vector Spaces and Linear Combinations#Basis|basis]] for a given vector space