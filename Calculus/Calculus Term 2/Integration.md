Section [[Calculus Term 2 (Root)]]
# Area Under a Curve

Given a **non-negative**, [[Differentiation#Continuity|continuous]] function $f(x)$, we can mathematically compute the area $I$ of the region bounded by the curve $y=f(x)$, $x=a$, $x=b$ and the $x$-axis

We can do a better job by splitting the range $[a,b]$ into $n$ strips, and forming a separate bound for each. We can look at the limit of the sum of the area of each strip as $n$ tends to infinity

We can define the **integral** like so:

Let $f$ be a non-negative, continuous function on $[a,b]$ and let $\{P_n\}$ be a sequence of finer partitions of $[a,b]$ such that $\Delta_i\rightarrow 0$ and $\xi_i$ be an arbitrary point in the $i^{th}$ subinterval. The **definite integral** of $f$ is defined like so:
$$\int^b_af(x)dx=\lim_{n\rightarrow\infty}\sum^n_{i=1}f(\xi_i)\Delta_i$$
Example - Find $\int^{b}_{a}x^2dx$ 

We'll use a partition $P_n$ which divides $[a,b]$ into $n$ even strips of width $\Delta=\frac{b-a}{n}$ and define $\xi=a+i\Delta$ (so the right-hand side of the strip)

To find the definite interval of $f$ on $[a,b]$, we evaluate the limit of the following sum:
$$\sum^n_{i=1}f(\xi_i)\Delta_i=\sum^n_{i=1}(a+i\Delta)^2\Delta$$
$$=na^2\Delta+2a\Delta^2(1+2+3+\dots+n)+\Delta^3(1^2+2^2+3^2+\dots+n^2)$$
$$=na^2\Delta+2a\Delta^2\frac{n(n+1)}{2}+\Delta^3\frac{n(n+1)(2n+1)}{6}$$
$$=a^2(b-a)+a(b-a)^2\frac{(n+1)}{n}+(b-a)^3\frac{(n+1)(2n+1)}{6n^2}$$$$\int^{b}_{a}f(x)dx=\lim_{n\rightarrow\infty}\sum^n_{i=1}f(\xi_i)\Delta_i=a^2(b-a)+a(b-a)^2+(b-a)^3\frac26$$
# Handling Discontinuity

Suppose $f$ is continuous on $[a,b]$ except at some point $c$, at which there is a discontinuity. We can no longer use the interval containing $c$ in our integral

Instead, we define two more integrals like so:
$$\int^{b}_{a}f(x)dx=\lim_{\epsilon\rightarrow0}\int^{c-\epsilon}_{a}f(x)dx+\lim_{\epsilon^\prime\rightarrow0}\int^{b}_{c+\epsilon^\prime}f(x)dx$$
Where **both** limits exist
# Negative Valued Functions

Suppose $f$ goes negative on an integral, we can simply define the area below the $x$-axis as **negative area**
# Piecewise Continuous

We looked at [[#Handling Discontinuity|discontinuity]], but how many of these can we deal with?

>[!quote] Definition
>A function $f$ is **piecewise continuous** on an interval $[a,b]$ if there is a set of **isolated** points $\{c_1.\dots,c_k\},c_1<c_2<\dots<c_k$ such that $f$ is continuous on $(a,c_1),(c_k,b)$ and all $(c_i,c_{i+1})$ from $i=1\dots k-1$



Well we can deal with a countably infinite set of these as long as they are **isolated**

>[!quote] Definition
>A set of points $\{c_1,\dots,c_k\}$ is **isolated** if there is some $\epsilon>0$ such that for all $i,j,1\leq i\leq j\leq k$ we have $|c_i-c_j|>\epsilon$

# Reimann Integral

The **Reimann Integral** uses the concepts explored in the [[#Piecewise Continuous|previous section]] to define an integral like so:
$$\int^{b}_{a}f(x)dx=\sum^k_{m=0}\int^{c_{m+1}}_{c_m}f(x)dx$$
# Properties of Definite Integrals
## Additivity with Respect to Range
$$\int^{b}_{a}f(x)dx=\int^{a}_{k}f(x)dx+\int^{k}_{b}f(x)dx$$
## Homogeneity
$$\int^{b}_{a}cf(x)dx=c\int^{b}_{a}f(x)dx$$
## Linearity
$$\int^{b}_{a}f(x)+g(x)dx=\int^{b}_{a}f(x)dx+\int^{b}_{a}g(x)dx$$
## Inequality
$$\forall x,x\in[a,b],f(x)\leq g(x)\implies\int^{b}_{a}f(x)dx\leq \int^{b}_{a}g(x)dx$$
# Mean Value Theorem

>[!quote] Theorem
>Let $f$ be a continuous function on $[a,b]$. There exists $\xi\in(a,b)$ such that:
>$$\int^{b}_{a}f(x)dx=(b-a)f(\xi)$$

# Indefinite Integrals

## Antiderivative

>[!quote] Definition
>A function $F$ such that $F^\prime(x)=f(x)$ is called the **antiderivative** of $f$

When defining the antiderivative we must remember a constant $C$ like so:
$$\int f(t)dt=F(x)+C$$
# Definite Integrals

We can evaluate **definite integrals** with any antiderivative like so:
$$\int^{b}_{a}f(x)dx=[F(x)]^b_a=F(b)-F(a)$$
A definite integral has specific bounds, and therefore is a value
# Improper Integrals

Consider $\int^{5}_{0}\frac{1}{x^2}dx$, with a **singularity** at $x=0$ (a point at which the function tends to $\pm\infty$)

If $f$ is continuous on $[a,b]$, except at some singularity $c$, then we define:
$$\int^{b}_{a}f(x)dx=\lim_{\epsilon\rightarrow0}\int^{c-\epsilon}_{a}f(x)dx+\lim_{\epsilon^\prime\rightarrow0}\int^{b}_{c+\epsilon^\prime}f(x)dx$$
## Divergent Integral

Now lets look at our previous integral:
$$\int^{5}_{0}\frac{1}{x^2}dx=\lim_{\epsilon\rightarrow0^+}\int^{5}_{\epsilon}\frac{1}{x^2}dx=\lim_{\epsilon\rightarrow0^+}\left[-\frac{1}{x}\right]^5_\epsilon=\lim_{\epsilon\rightarrow0^+}\left(-\frac{1}{5}+\frac{1}{\epsilon}\right)=+\infty$$
Here we see the integral **diverges**
## Convergent Integral

The following integrand is undefined when $x=0$:
$$\int^{2}_{-1}\frac{1}{\sqrt{|x|}}dx$$
Lets split the interval at $0$ and take both limits:
$$\int^{2}_{-1}\frac{1}{\sqrt{|x|}}dx=\lim_{\epsilon\rightarrow0}\int^{-\epsilon}_{-1}\frac{1}{\sqrt{|x|}}dx+\lim_{\epsilon^\prime\rightarrow0}\int^{2}_{+\epsilon^\prime}\frac{1}{\sqrt{|x|}}dx$$
Then we guess our antiderivative for both integrals and look at our limits:
$$\int^{2}_{-1}\frac{1}{\sqrt{|x|}}dx=\lim_{\epsilon\rightarrow0}\left[-2\sqrt{-x}\right]^{-\epsilon}_{-1}+\lim_{\epsilon^\prime\rightarrow0}\left[2\sqrt{x}\right]^{2}_{\epsilon^\prime}$$
$$\lim_{\epsilon\rightarrow0}\left[-2\sqrt{\epsilon}+2\sqrt1\right]+\lim_{\epsilon^\prime\rightarrow0}\left[2\sqrt{2}-2\sqrt{\epsilon^\prime}\right]=2+2\sqrt2$$
See we need to use two different limits, $\epsilon$ and $\epsilon^\prime$, because we shouldn't be able to cancel them out
## Infinity Bounds

We can use limits on the bounds themselves to look at integrals with infinite bounds like so:
$$\int^{\infty}_{a}f(x)dx=\lim_{N\rightarrow\infty}\int^N_af(x)dx$$
or
$$\int^{\infty}_{-\infty}f(x)dx=\lim_{N\rightarrow\infty}\int^a_{-N}f(x)dx+\lim_{N^\prime\rightarrow\infty}\int^{N^\prime}_af(x)dx$$
Now check these out:
$$\int^{\infty}_{2}\frac{1}{x^2}dx=\lim_{N\rightarrow\infty}\int^N_2\frac{1}{x^2}dx=\lim_{N\rightarrow\infty}\left[-\frac{1}{x}\right]^N_2=\lim_{N\rightarrow\infty}\left(-\frac{1}{N}+\frac{1}{2}\right)=\frac{1}{2}$$
$$\int^{\infty}_{2}\frac{1}{x}dx=\lim_{N\rightarrow\infty}\int^N_2\frac{1}{x}dx=\lim_{N\rightarrow\infty}\left[\ln x\right]^N_2=\lim_{N\rightarrow\infty}\left(\ln N-\ln 2\right)=\infty$$
Seem [[Introduction to Series#Convergence|familiar]]? Remember that $\sum^{\infty}_{n=1}\frac{1}{n^2}$ **converges**, but $\sum^{\infty}_{n=1}\frac{1}{n}$ **diverges**
## Integral Test for Series Convergence

>[!quote] Definition
>If $f$ is a continuous, decreasing, positive function on $[m,\infty)$ then
>- If $\int^{\infty}_{m}f(x)dx$ is **convergent** then so is $\sum^{\infty}_{n=m}f(n)$
>- If $\int^{\infty}_{m}f(x)dx$ is **divergent** then so is $\sum^{\infty}_{n=m}f(n)$

# Systematic Integration
## Integration of Elementary Functions

| $f(x)$         | $F(x)$                |
| -------------- | --------------------- |
| $a$            | $ax$                  |
| $x^n,n\neq -1$ | $\frac{x^{n+1}}{n+1}$ |
| $x^{-1}$       | $\ln \|x\|$           |
| $e^{ax}$       | $\frac{1}{a}e^{ax}$   |
| $\sin ax$      | $-\frac{1}{a}\cos ax$ |
| $\cos ax$      | $\frac{1}{a}\sin ax$  |
| $\sinh ax$     | $\frac{1}{a}\cosh ax$ |
| $\cosh ax$     | $\frac{1}{a}\sinh ax$ |
## Integration by Substitution

This works similarly to the [[Differentiation#Chain Rule|chain rule]]. Suppose we spot an integrand in the form $f(u(x))u^\prime(x)$ and take $F(u)$ to be the antiderivative of $f(u)$, then:
$$\frac{dF}{dx}=\frac{DF}{du}\frac{du}{dx}=f(u)u^\prime(x)$$
hence $F(u(x))$ is the **antiderivative** of $f(u(x))u^\prime(x)$
$$\int f(u(x))u^\prime(x)dx=\int f(u)dx$$
Example - Find $\int \frac{4x}{\sqrt{2x^2+1}}dx$ 

We can recognise this as substitution because:
$$\frac{4x}{\sqrt{2x^2+1}}=f(u)\frac{du}{dx}\;\;,\;\;u=2x^2+1\;\;,\;\;f(u)=\frac{1}{\sqrt u}$$
So:
$$\int \frac{4x}{\sqrt{2x^2+1}}dx=\int\frac{1}{\sqrt u}du=2\sqrt u+C=2\sqrt{2x^2+1}+C$$
## Integration by Parts

Recall the [[Differentiation#Product Rule|product rule]]. If $u$ and $v$ are functions of $x$ then:
$$\frac{duv}{dx}=\frac{du}{dx}v+\frac{dv}{dx}u$$
Therefore $uv$ is the **antiderivative** of $u^\prime v+uv^\prime$, lets rearrange this a bit using the [[#Linearity|linearity]] of integrals:
$$\int u^\prime v+uv^\prime\;dx=\int u^\prime v\;dx+\int uv^\prime\;dx=uv+C$$
$$\int uv^\prime \;dx=uv-\int u^\prime v\;dx$$
Example - Find $\int x^k\ln x \;dx$
$$\int x^k\ln x \;dx=\int uv^\prime\;dx$$
Now we need to be careful as to which product we choose to be $u$ and $v^\prime$, since one is to be **integrated** and the other to be **differentiated**

Were we to integrate $\ln x$, we'd get something with more $\ln x$ in it. *But*, if we differentiate $\ln x$ and integrate $x^k$ we get the following:
$$u=\ln x,v^\prime=x^k\therefore u^\prime=\frac{1}{x},v=\frac{x^{k+1}}{k+1}$$
This is looking very cancel-out-able, now check this out:
$$uv-\int u^\prime v\;dx=\frac{x^{k+1}}{k+1}\ln x-\int \frac{1}{x}\frac{x^{k+1}}{k+1}dx=\frac{x^{k+1}}{k+1}\ln x-\int\frac{x^{k}}{k+1}dx$$
Finally we integrate our new integrand to get:
$$\frac{x^{k+1}}{k+1}\ln x-\int\frac{x^{k}}{k+1}dx=\frac{x^{k+1}}{k+1}\ln x-\frac{x^{k+1}}{(k+1)^2}+C$$