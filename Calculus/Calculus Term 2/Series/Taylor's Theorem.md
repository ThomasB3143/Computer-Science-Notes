Section: [[Series (Root)]]

Recall that we can represent a function as a [[Power Series#Taylor Series|Taylor series]]

When forming [[Power Series#Maclaurin Series|Maclaurin]] and [[Power Series#Taylor Series|Taylor]] series, it was clarified that **if** a series exists for a function, **then** it has these coefficients. This does not prove that the series converges to the correct value. Hence we need to find out when a series is actually equal to the function it is representing
# Quadratic Approximation

Starting with a function $f(x)$, we can determine a **quadratic form** such that near $x_0$:
$$f(x)\approx a_0+a_1(x-x_0)+a_2(x-x_0)^2$$
We know the following:

- $f(x_0)=a_0$
- $f^\prime(x_0)=a_1$
- $f^{\prime\prime}(x_0)=2a_2$

Putting this together, we have:
$$f(x)\approx f(x_0)+f^\prime(x_0)(x-x_0)+\frac{f^{\prime\prime}(x_0)}{2}(x-x_0)^2$$
This forms the [[Power Series#Taylor Series|Taylor series]] expansion of $f$, if $f$ is equal to a power series:
$$f(x)=\sum_{n=0}^\infty f^{(n)}(x_0)\frac{(x-x_0)^n}{n!}$$
Note that the [[Power Series#Maclaurin Series|Maclaurin expansion]] is a special case where $x_0=0$
# Taylor's Theorem

When we came up with the Taylor series, we said that **if** a series exists that is equal to $f$, **then** it must have these coefficients. That doesn't prove that the series converges to the correct value

So we need a way of knowing when our Taylor series is *actually* equal to the function we got it from

Let $f(x)$ be a smooth function with a Taylor series representation:
$$f(x)=\sum_{n=0}^\infty f^{(n)}(x_0)\frac{(x-x_0)^n}{n!}$$
Let $P_{n-1}=\sum_{i=0}^{n-1} f^{(i)}(x_0)\frac{(x-x_0)^i}{i!}$ be the sum of the first $n$ terms, terminating at the term of $(x-x_0)^{n-1}$

A Taylor series will converge to $f(x)$ if, and only if:
$$\lim_{n\rightarrow\infty}|f(x)-P_{n-1}(x)|=0$$
So we're just looking at the remainder of the series after $n$ terms, to establish **convergence**

>[!quote] Definition
>Suppose a function $f$ is differentiable on $[a,x]$, then there exists some $\xi\in(a,x)$ such that:
>$$f(x)=f(a)+(x-a)f^\prime(a)+\dots+\frac{(x-a)^{n-1}}{(n-1)!}f^{(n-1)}(a)+\frac{(x-a)^n}{n!}f^{(n)}(\xi)$$

We can prove this using...
## Rolle's Theorem

>[!quote] Definition
>If a real-valued function $f$ is continuous and differentiable on $[a.b]$, and $f(a)=f(b)$, then there exists $\xi\in(a,b)$ such that $f^\prime(\xi)=0$

## Example of Taylor's Theorem

$f(x)=\sin x$, find a power series expansion of $f$ and show that it **converges**
$$f(0)=0$$
$$f^\prime(0)=\cos(0)=1$$
$$f^{\prime\prime}(0)=-\sin(0)=0$$
$$f^{(3)}(0)=-\cos(0)=-1$$
$$\sin x=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\frac{x^7}{7!}+\dots+\frac{x^n}{n!}\sin^{(n)}\xi$$
Since $|\sin^{(n)}\xi|\leq 1$ we have $\lim_{n\rightarrow\infty}\frac{x^n}{n!}\sin^{(n)}\xi=0$, so the series converges to $\sin x$
# L’Hôpital’s Rule

>[!quote] Definition
>Let $f$ and $g$ be $n$-times differentiable functions such that:
>- $f(a)=g(a)=0$
>- $f^{(r)}(a),g^{(r)}(a)=0$ for $1\leq r\leq n-1$
>- $f^{(n)}(a),g^{(n)}(a)$ are not zero
>Then
>$$\lim_{x\rightarrow a}\frac{f(x)}{g(x)}=\lim_{x\rightarrow a}\frac{f^{(n)}(x)}{g^{(n)}}(x)$$

