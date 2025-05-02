Section: [[Series (Root)]]

Recall that we can represent a function as a [[Power Series#Taylor Series|Taylor series]]

When forming [[Power Series#Maclaurin Series|Maclaurin]] and [[Power Series#Taylor Series|Taylor]] series, it was clarified that **if** a series exists for a function, **then** it has these coefficients. This does not prove that the series converges to the correct value. Hence we need to find out when a series is actually equal to the function it is representing:

Let $f(x)$ have the Taylor series representation $\sum\limits^\infty_{n=0}f^{(n)}(x_0)\frac{(x-x_0)^n}{n!}$ and let $P_{n-1}(x)$ be the sum of the first $n$ terms. Then it is necessary that, for $f(x)$ to converge, that $\lim\limits_{n\rightarrow\infty}|f(x)-P_{n-1}(x)|=0$

Suppose a function $f$ is $n$ times differentiable on $[a,x]$, then there is some $\omega\in(a,x)$ such that:

$f(x)=f(a)+(x-a)f^\prime(a)+\dots+\frac{(x-a)^n}{n!}f^{(n)}(\omega)$ 

So a necessary condition for the Taylor series to converge to $f(x)$ is that $\lim\limits_{n\rightarrow\infty}|R_n(x)|=0$

