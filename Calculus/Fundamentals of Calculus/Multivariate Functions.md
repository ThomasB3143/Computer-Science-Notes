Section: [[Fundamentals of Calculus (Root)]]

We can view a function with **two** variables as a 2D surface in 3D space like so:

$f(x,y)=\sin x + \cos y + 1.5$

![[Pasted image 20250504150233.png]]

We may want to find:

- The gradient in a direction
- The limit of $f$ as we approach a given $(x,y)$
- The direction of steepest ascent from a point
- A linear approximation to a surface at a point

Consider $f(x,y)=2x^2y^3-xy+2x-3y+5$, and try fixing one of the variables:

- $y=0\implies f(x,0)=2x+5$
- $y=1\implies f(x,0)=2x^2+x+2$
- $x=0\implies f(0,y)=-2y+5$
- $x=1\implies f(1,y)=2y^3-4y+7$
# Partial Derivative

>[!quote] Definition
>The **partial derivative** of a function $f$ with respect to a variable $x$ is found by fixing all other variables and [[Differentiation|differentiating]] as normal

Consider our previous example, lets fix $y=y_0$ and differentiate with respect to $x$:

$$\frac{\delta f}{\delta x}(x_0,y_0)=\lim_{x\rightarrow x_0}\frac{f(x,y_0)-f(x_0,y_0)}{x-x_0}$$
Hence:
$$\frac{\delta f}{x}(2x^2y^3-xy+2x-3y+5)=4y^3x-y+2$$
Note that the result of this function shows the gradient in the **$x$-direction**. We may wite this as $f_x$ for short
## Continuity and Partial Derivatives

It is important to note that the existence of partial derivatives of all variables does **not** imply [[Differentiation#Continuity|continuity]]
# Directional Derivatives

Consider a point $x_0=(x_0y_0)$ and a direction given as a **unit vector** $v=\binom{v_x}{v_y}$. The **directional derivative** is given as:
$$\nabla_vf(x_0,y_0)=\lim_{h\rightarrow 0}\frac{f(x_0+hv_x,y_0+hv_y)-f(x_0,y_0)}{h}=\lim_{h\rightarrow 0}\frac{f(x_0+hv)-f(x_0)}{h}$$ This gives the gradient of the slope of $f$ if you were to move in the $\boldsymbol{v}$ direction through point $\boldsymbol{x_0}=(x_0,y_0)$

Example - what is the gradient in the direction at $\begin{pmatrix}\frac{1}{\sqrt{5}}\\\frac{2}{\sqrt{5}}\end{pmatrix}{}$ through $(1,3)$?
$$\lim_{h\rightarrow 0}\frac{f(1+h\frac1{\sqrt5},3+h\frac{2}{\sqrt5})-f(1,3)}{h}$$
$$\lim_{h\rightarrow 0}\frac{2(1+h\frac1{\sqrt5})^2(3+h\frac{2}{\sqrt5})^3-(1+h\frac1{\sqrt5})(3+h\frac{2}{\sqrt5})+2(1+h\frac1{\sqrt5})-3(3+h\frac{2}{\sqrt5})+5-49}{h}$$
$$\lim_{h\rightarrow 0}\frac{h\frac{207}{\sqrt5}+h^2+\dots}{h}=\frac{207}{\sqrt5}$$
However, if the slope is approximately flat at a small scale, we can determine the slope in any direction using the [[#Directional Derivatives]] of each variable like so:

$$v_xf_x+v_yf_y=\boldsymbol{v}\begin{pmatrix}
f_x\\f_y
\end{pmatrix}=\nabla_vf$$
We say $f$ is **differentiable** if this equation holds for all unit vectors at a point

The vector of [[#Partial Derivative|partial derivatives]] is denoted $\nabla f$, and also happens to have both the **direction** and **magnitude** of the greatest rate of increase of $f$
# Linear Approximations

For **univariate** functions, the derivative gives qualities of the **tangent**. Since $$f(\boldsymbol{x_0}+h\boldsymbol{v})\approx f(\boldsymbol{x_0})+h\boldsymbol{v}\nabla f(\boldsymbol{x_0})$$
# More Variables

We have only been considering functions with 2 variables, that give rise to a 2D surface, lets get even more complicated

A 3D function, will give rise to a 3D space with a value at each point, useful for representing things such as the heat in a room

Any $n$ dimensional function gives rise to a $n$ dimensional surface in $n+1$ dimensional space
# Multivariate Chain Rule

Recall [[Differentiation#Chain Rule|chain rule]]. We can look at an example to understand this for a **multivariate**

Suppose $f(x,y):\mathbb{R}^2\mapsto\mathbb{R}$ such that $x$ and $y$ are functions of $s$ and $t$. How do we find $\frac{\delta f}{\delta t}$
$$\frac{\delta f}{\delta t}=\frac{\delta f}{\delta x}\frac{\delta x}{\delta t}+\frac{\delta f}{\delta y}\frac{\delta y}{\delta t}$$