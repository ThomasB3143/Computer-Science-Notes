Section: [[Discrete Term 1 (Root)]]

Generating functions encode combinatorial information in an analytical form

Example - $(1+x)^n=\sum\limits_{k=0}^n\binom{n}{k}x^k$

This function basically encodes the counting info $\binom n0,\binom n1\dots\binom nn$ as the coefficients in the power series

So where $a_0,a_1,a_2,\dots a_k$ is a sequence of real numbers, he generating function is like so:

$f(x)=\sum\limits_{k=0}^\infty a_kx^k$

This lets us do funky calculus and manipulate the sum without worrying about power series convergence (because it is a **formal** sum)

## Counting

This can solve some tough combinatorial problems, such as ones where we need a combination to sum to a particular value\\

Example - 7 chocolate bars distributed amongst 4 people. one person has a max of 4, one a max of 3, one a max of 2, and one a max of 1. How many ways can we distribute the bars?

So we want solutions for all $e_i$, where $e_1+e_2+e_3+e_4=7$

$e_i$ is the number of chocolate bars given to person $i$

What we can do is represent $e_i$ as $\sum\limits_{n=1}^kx^{a_k}$ where $a_1,\dots,a_k$ are all values that $e_i$ can take. Using this idea, we get:

$f(n)=(x^0+x^1+x^2+x^3+x^4)(x^0+x^1+x^2+x^3)(x^0+x^1+x^2)(x^0+x^1)$

Each term in $f(n)$ is a possible product

$x^{e_1}x^{e_2}x^{e_3}x^{e_4}=x^{e_1+e_2+e_3+e_4}=x^7$

So the number of solutions is the number of ways to get $x^7$ by choosing a term from each factor of $f(x)$. This means that the number of solutions is the coefficient of $x^7$ in the expansion of $f(n)$

Now, we need some important tools to expand $f(n)$ into a generating function where the coefficient of all $x^p$ are easily obtained. Here are some incredibly important equations to do so:

1. $(1+x)^n=\sum\limits_{k=0}^n\binom nkx^k$
2. $(1+x+\dots+x^r)^n=\left(\frac{1-x^{r+1}}{1-x}\right)^n$
3. $(1-x)^{-n}=\sum\limits_{k=0}^\infty\binom{n+k-1}{k}x^k$

Example of use - identify the coefficients of $(1+x+x^2)^3$

$(1+x+x^2)^3=\left(\frac{1-x^3}{1-x}\right)^3=(1-x^3)^3(1-x)^{-3}$
$(1-x^3)^3=\sum\limits^3_{i=0}\binom 3i(-x^3)^i,(1-x)^{-3}=\sum\limits^\infty_{k=0}\binom{3+k-1}{k}x^k$
$f(x)=\sum\limits^3_{i=0}\binom 3i(-x^3)^i\sum\limits^\infty_{k=0}\binom{k+2}{k}x^k=\sum\limits_{j=0}^\infty a_jx^j$

If we want to find the coefficient of the term $x^4$ we look at the combinations $i=1,k=1$ and $i=0,k=4$ since $x^j=x^{3i+k}=x^4$

Therefore the coefficient of $x^4$ in $f(x)$ will be:

$\binom31(-1)^1\binom31+\binom30(-1)^0\binom64=6$
## Recurrence Relations

Recall what a [[Recurrence Relations|recurrence relation]] is, we can use generating functions to solve these.

Example - Solve the recurrence relation $a_n=a_{n-1}+2a_{n-2},n\geq2,a_0=1,a_1=-1$

We need to write the generating function for $a_n$ as $f(x)=\sum\limits^\infty_{n=0}a_nx^n$. In this sum, we can replace $a_n$ with the recurrence relation (only for values of $n$ that are valid, you can tidy this up using the **initial conditions**) like this:

$f(x)=a_0+a_1x+\sum\limits^\infty_{n=2}a_nx^n$
$f(x)=1-x+\sum\limits^\infty_{n=2}(a_{n-1}+2a_{n-2})x^n$
$f(x)=1-x+\sum\limits^\infty_{n=2}a_{n-1}x^n+\sum\limits^\infty_{n=2}2a_{n-2}x^n$
$f(x)=1-x+x\sum\limits^\infty_{n=2}a_{n-1}x^{n-1}+2x^2\sum\limits^\infty_{n=2}a_{n-2}x^{n-2}$
$f(x)=1-x+x\sum\limits^\infty_{n=1}a_{n}x^{n}+2x^2\sum\limits^\infty_{n=0}a_{n}x^{n}$
$f(x)=1-x+x(\sum\limits^\infty_{n=0}a_{n}x^{n}-a_0)+2x^2\sum\limits^\infty_{n=0}a_{n}x^{n}$
$f(x)=1-x+x(\sum\limits^\infty_{n=0}a_{n}x^{n}-1)+2x^2\sum\limits^\infty_{n=0}a_{n}x^{n}$

But remember that $f(x)=\sum\limits^\infty_{n=0}a_nx^n$:

$f(x)=1-x+x(f(x)-1)+2x^2f(x)=1-x+xf(x)-x+2x^2f(x)$
$f(x)(2x^2+x-1)=2x-1$
$f(x)(2x-1)(x+1)=2x-1$
$f(x)=\frac{1}{1+x}=(1-(-x))^{-1}=\sum\limits^\infty_{k=0}\binom{k}{k}(-1)^kx^k$
$f(x)=\sum\limits^\infty_{k=0}(-1)^kx^k=1-x+x^2-x^3+x^4+\dots$

So we can see that $a_n$ alternates between $1$ and $-1$
## Partitions

A partition of a positive integer $n$ is an expression of $n$ as an **unordered** sum of positive integers (where each integer is a **part**). The number of partitions of $n$ is $p(n)$
### Finding $p(n)$

I'll save you the time of thinking about it, we actually don't know how to do this. But we know that:

$p(n)\approx\frac{1}{4n\sqrt3}\exp\left(\pi\sqrt{\frac{2n}{3}}\right)$ as $n\rightarrow\infty$

But if the parts are distinct, then each integer will either appear or not appear, hence we have the following function:

$(1+x)(1+x^2)(1+x^3)+\dots=\prod\limits^\infty_{k=1}(1+x^k)$

However when not distinct we have:

$\prod\limits^\infty_{k=1}(1+x^k)^{-1}=\sum\limits^\infty_{n=0}x^np(n)$
## Calculus

We can bridge discrete and continuous mathematics by performing calculus on generating functions

Example - Find the generating function of the sequence $a_n=n$

$f(x)=\sum\limits^\infty_{n=0}nx^n=x\sum\limits^\infty_{n=0}nx^{n-1}$
$f(x)=x\frac{\partial}{\partial x}(\sum\limits^\infty_{n=0}x^n)$
$f(x)=x\frac{\partial}{\partial x}(\frac{1}{1-x})$
$f(x)=\frac{x}{(1-x)^2}$

We can use these handy theorems:

If $f(x)=\sum\limits^\infty_{n=0}a_nx^n$ then the generating function for $b_n=na_n$ is $xf^\prime(x)$

If $f(x)=\sum\limits^\infty_{n=0}a_nx^n$ then the generating function for $s_n=\sum\limits^n_{k=0}a_k$ is $\frac{f(x)}{1-x}$

