Section: [[Fundamentals of Calculus (Root)]]

>[!quote] Definition
>The **derivative** of a function $f(x)$ at a point $x=x_0$ is the instant rate of change of $f$ at the point $x_0$, also known as the **gradient**

The gradient at $x_0$ may be approximated by $\frac{f(x)-f(x_0))}{x-x_0}$, and the closer we take $x$ to $x_0$ the better the approximation

>[!quote] Theorem
>$f$ is differentiable at $x=x_0$ if, and only if, $\lim_{x\rightarrow x_0}\frac{f(x)-f(x_0))}{x-x_0}$ exists
>

Equivalently, the derivative is $\lim_{h\rightarrow 0}\frac{f(x_0+h)-f(x_0))}{h}$

The derivative of $f(x)$ is denoted $f^\prime(x)$ or $\frac{\partial f}{\partial x}$
## Basic Derivatives

| $f(x)$      | $f^\prime(x)$             |
| ----------- | ------------------------- |
| $c$         | $0$                       |
| $ax$        | $a$                       |
| $x^n$       | $nx^{n-1}$                |
| $\sin ax$   | $a\cos ax$                |
| $\cos ax$   | $-a\sin ax$               |
| $g(x)+h(x)$ | $g^\prime(x)+h^\prime(x)$ |
# One-Sided Limits

Suppose a function has a **kink** in it, where the derivate changes immediately at a point (like a corner). We need a way to separate the derivate on the **left** to the one on the **right**

We write $\lim_{h\rightarrow 0^+}$ for the limit restricted to **positive** $h$ and $\lim_{h\rightarrow 0^-}$ for limits restricted to **negative** $h$
# Continuity

>[!quote] Definition
>A function $f$ is **continuous** at $x=a$ if $f(x)=\lim_{h\rightarrow 0^+}=\lim_{h\rightarrow 0^-}$

We can state a function to be continuous on an [[Sets and Functions#Intervals|interval]] if it is continuous at all points in the interval
# Differentiability

>[!quote] Definition
>A function $f$ is **differentiable** at $x=a$ if $\lim_{x\rightarrow a}\frac{f(x)-f(a)}{x-a}$ exists, this means $f$ must be [[#Continuity|continuous]] at $x=a$

We denote the derivative of the derivative of $f$ as $f^{\prime\prime}$ or $f^{(2)}$, then $f^{\prime\prime\prime}$ or $f^{(3)}$ and so on.
## Smoothness

>[!quote] Definition
>A function is **smooth** if all $f^{k}$ are [[#Differentiability|differentiable]]

# Differentiation Rules
## Product Rule

>[!quote] Theorem
>If $f(x)$ and $g(x)$ are **differentiable** at a point, then so is $f(x)g(x)$. Furthermore, $\frac{\partial f(x)g(x)}{\partial x}$ at this point is equal to $f^\prime(x)g(x)+f(x)g^\prime(x)$
## Quotient Rule

>[!quote] Theorem
>If $f(x)$ and $g(x)$ are **differentiable** at a point, then so is $\frac{f(x)}{g(x)}$. Furthermore, $\frac{\partial f(x)/g(x)}{\partial x}$ at this point is equal to $\frac{f^\prime(x)g(x)-g^\prime(x)f(x)}{g(x)^2}$
## Chain Rule

>[!quote] Theorem
>If $f(x)$ and $g(x)$ are **differentiable** at a point, then so is $f(g(x))$. Furthermore, $\frac{\partial f(g(x))}{\partial x}$ at this point is equal to $g^\prime(x)f^\prime(g(x))$

It is often needed to set a variable $u=g(x)$ and use the following equation:

$$\frac{\partial f}{\partial x}=\frac{\partial f}{\partial u}\frac{\partial u}{\partial x}$$
# Extrema

Let $f(x)$ be a function defined on an interval $[a,b]$, a point $x_0$ is:

- An **absolute maximum** if $f(x_0)\geq f(x)\forall x\in[a,b]$
- An **absolute minimum** if $f(x_0)\leq f(x)\forall x\in[a,b]$
- A **local maximum** if $\exists \delta>0:f(x_0)\geq f(x_0+h)\forall |h|<\delta$
- A **local minimum** if $\exists \delta>0:f(x_0)\leq f(x_0+h)\forall |h|<\delta$
## Stationary Points

At these **minima** and **maxima**, $f^\prime(x)=0$. These are called **stationary points**