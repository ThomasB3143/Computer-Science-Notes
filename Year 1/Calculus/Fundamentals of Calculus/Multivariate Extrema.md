Section: [[Fundamentals of Calculus (Root)]]
# Second Derivatives

Consider a [[Differentiation#Stationary Points|stationary point]] on a function $f$. We know that $f^\prime=0$ at that point, but we need to know the **second derivative** $f^{\prime\prime}$ to determine its **nature**:

- $f^{\prime\prime}>0\implies$ gradient is increasing $\therefore$ we have a [[Differentiation#Extrema|minima]]
- $f^{\prime\prime}<0\implies$ gradient is decreasing $\therefore$ we have a [[Differentiation#Extrema|maxima]]
- $f^{\prime\prime}=0\implies$ gradient is not changing $\therefore$ we **may** have a point of **inflection**

```functionplot
---
title: Inflection at (2,1)
xLabel: 
yLabel: 
bounds: [1,3,0,2]
disableZoom: false
grid: true
---
f(x)=(x-2)^3+1
```
# Quadratic Approximations

Recall that the gradient gives a **linear approximation** to $f$ like so:
$$f(x_0+x)\approx f(x_0)+f^\prime(x_0)x$$
The curvature can give a **quadratic approximation** like so:
$$f(x_0+x)\approx f(x_0)+f^\prime(x_0)x+\frac{f^{\prime\prime}(x_0)}{2}x^2$$

```functionplot
---
title: Example
xLabel: 
yLabel: 
bounds: [-5,2,-2,3]
disableZoom: false
grid: true
---
f(x)=x^3/3+2x^2+3x+1
g(x)=(x+1)^2-0.333
```
# Smoothness and Higher Order Derivatives

Recall [[Differentiation#Smoothness|smoothness]]. A function such that $f^{(k)}$ exists is in class $C^k$. One that is $C^\infty$ is considered **smooth** 
## Higher Order Derivatives of Multivariates

When we differentiate a multivariate repeatedly, we need to choose a variable each time. For example, $f(x,y)$ will have the following second derivatives:

- $f_{xx}$
- $f_{yy}$
- $f_{xy}$
- $f_{yx}$
## Bivariate Extrema

It is not enough to examine one second order derivative to determine the nature of a stationary point on a bivariate graph. We need to examine the second order derivative of both variables like so:

| $f_{xx}$ | $f_{yy}$ | Nature  |
| -------- | -------- | ------- |
| positive | positive | minimum |
| negative | negative | maximum |
| positive | negative | saddle  |
| negative | positive | saddle  |
# Hessian Matrix

But this is not enough, we need to consider **all** partial derivates. To do this, we construct **Hessian matrix** $H_f$ for $f$:
$$\begin{bmatrix}
f_{xx}&f_{yx}\\
f_{xy}&f_{yy}
\end{bmatrix}$$
This now contains information about curvature in all directions
>[!quote] Theorem
> Given $f(x,y)$ where $f_x(x_0,y_0)=f_y(x_0,y_0)=0$ then $(x_0,y_0)$ is:
> - a local **maximum** if $f_{xx}f_{yy}-f^2_{xy}>0$ and $f_{xx}<0$
> - a local **minimum** if $f_{xx}f_{yy}-f^2_{xy}>0$ and $f_{xx}>0$
> - a **saddle point** $f_{xx}f_{yy}-f^2_{xy}<0$
>If $f_{xx}f_{yy}-f^2_{xy}=0$ then the test is inconclusive (we need to look at **higher orders**)

You may notice that $f_{xx}f_{yy}-f^2_{xy}$ is the **determinant** of $H_f$ for a smooth function 







