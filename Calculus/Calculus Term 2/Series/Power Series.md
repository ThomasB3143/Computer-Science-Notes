Section: [[Series (Root)]]

An infinite sum of terms involving powers of $x$ in the form:

$\sum\limits^\infty_{n=0}a_n(x-x_0)^n$

where $a_n$ are the **coefficients** of the series and $x_0$ is the **center**.

## Converging

Converges for specific values of $x$, possibly:

- For all $x\in\mathbb{R}$
- For certain $x$ within a range
- Only for $x=x_0$ (because all terms are $0$ and technically convergent)

## Radius of Convergence

Denoted by $r$, this tells us the values of $x$ around $x_0$ that the series will converge for:

$r=\lim\limits_{n\rightarrow\infty}|\frac{a_n}{a_{n+1}}|$

When $x_0-r< x< x_0+r$ , the series will converge, but when $x=x_0-r,x_0+r$ we need to do another [[Introduction to Series#Tests of Convergence|test]] to determine if the series will converge.

IMPORTANT NOTE: If $r=\infty$ then the series will converge for all $x\in\mathbb{R}$

Example:

For what real values of $x$ will the power series $\sum\limits^\infty_{n=0}\frac{x^n}{n}$ converge?
$x_0=0,a_n=\frac1n$ 
$r=\lim\limits_{n\rightarrow\infty}|\frac{n+1}{n}|=\lim\limits_{n\rightarrow\infty}|1+\frac{1}{n}|=1$
$\therefore$ converges for $x\in(-1,1)$

## Differentiation and Integration

Where $f(x)=\sum\limits^\infty_{n=0}a_nx^n$ is a power series such that $r>0$, then within the interval $(-r,r)$:

- $f(x)$ is continuous
- $f^\prime(x)=\sum\limits^\infty_{n=0}na_nx^{n-1}$
- $\int^x_0f(t)dt=\sum\limits^\infty_{n=0}\frac{a_n}{n+1}x^{n+1}$ 
- Both have the same radius of convergence as $f(x)$

## Power Series from Functions

Given any $f(x)$, we want to find the power series such that $f(x)=\sum\limits^\infty_{n=0}a_nx^n$ 

It makes sense to say that when $x=0$, $a_0=f(0)$
and $f^\prime(0)=a_1$
and $f^{\prime\prime}(0)=2a_2$
and $f^{\prime\prime\prime}(0)=6a_3$
so $f^{(m)}(0)=m!a_m$

### Maclaurin Series

$f(x)=f(0)+f^\prime(0)x+f^{\prime\prime}(0)\frac{x^2}{2!}+\dots$
$\therefore f(x)=\sum\limits^\infty_{n=0}f^{(n)}(0)\frac{x^n}{n!}$
$f$ must be smooth (can be differentiated an infinite number of times) and the power series must converge

Example:

$f(x)=\ln(x+1)$

$f^\prime(x)=\frac{1}{x+1},f^{\prime\prime}(x)=-\frac{1}{(x+1)^2},f^{\prime\prime\prime}(x)=\frac{1}{(x+1)^3}\therefore f^{(n)}(x)=(-1)^{n+1}\frac{(n-1)!}{(x+1)^n}$

$\therefore f^{(n)}(0)=(-1)^{n+1}(n-1)!$

Therefore the Maclaurin series for $f$ is

$\ln(x+1)=f(0)+\sum\limits^\infty_{n=1}f^{(n)}(0)\frac{x^n}{n!}=\sum\limits^\infty_{n=1}(-1)^{n+1}\frac{x^n}{n}$
### Taylor Series

Same as Maclaurin but we recentre away from $0$ to $x_0$

$g(x)=f(x+x_0)\therefore g^{(m)}(x)=f^{(m)}(x+x_0)$
$g(0)=f(x_0)\therefore g^{(m)}(0)=f^{(m)}(x_0)$

$f(x+x_0)=g(x)=\sum\limits^\infty_{n=0}g^{(n)}(0)\frac{x^n}{n!}=\sum\limits^\infty_{n=0}f^{(n)}(x_0)\frac{x^n}{n!}$
or
$f(x)=g(x-x_0)=\sum\limits^\infty_{n=0}g^{(n)}(0)\frac{(x-x_0)^n}{n!}=\sum\limits^\infty_{n=0}f^{(n)}(x_0)\frac{(x-x_0)^n}{n!}$

Example:

$f(x)=x\ln(x)$

$f^\prime(x)=1+\ln x,f^{\prime\prime}(x)=\frac1x,f^{\prime\prime\prime}(x)=-\frac{1}{x^2}\therefore f^{(n)}(x)=(-1)^n\frac{(n-2)!}{x^{n-1}}$

These are all undefined when $x=0$ so we have to make a **Taylor series** at $x_0=1$

$f(1)=0,f^\prime(1)=1,f^{\prime\prime}(1)=1\therefore f^{(n)}(1)=(-1)^n(n-2)!$

Therefore the Taylor series for $f$ is
$\sum\limits^\infty_{n=0}f^{(n)}(x_0)\frac{(x-x_0)^n}{n!}=\sum\limits^\infty_{n=0}(-1)^n(n-2)!\frac{(x-1)^n}{n!}=\sum\limits^\infty_{n=0}\frac{(-1)^n(x-x_0)^n}{n(n-1)}=\sum\limits^\infty_{n=0}\frac{(x_0-x)^n}{n(n-1)}$
This will have a radius of convergence $r=1$ and converges on $[0,2]$ 