Section: [[Calculus Term 2 (Root)]]

Suppose we have a function $f$ (our **objective function**) where any given input must follow a **constraint** function $g$. What if we want to maximise the output of $f$ whilst following our constraint $g$

Here is an easy example:


$$f(x,y)=x^2+y^2 \text{  is subject to  } x=2-y$$
$$h(y)=(2-y)^2+y^2=2y^2-4y+4$$
$$h^\prime(y)=4y-4=0$$
$$y=1\therefore x=1$$
So $f$ is minimised at $(1,1)$! 

When we want the min/max of our objective function $f$, subject to a restraint $g$, the gradient vectors of $f$ and $g$ must be **parallel**. Therefore:
$$\exists\lambda\in\mathbb{R}:\nabla f=\lambda\nabla g$$
Our optimisation problem is now represented as a system of equations!
$$\nabla f=\lambda\nabla g\implies
\begin{cases} 
      f_x=\lambda g_x\\
      f_y=\lambda g_y\\
      g=0 
   \end{cases}$$
We have three equations and three unknowns, $x$, $y$ and $\lambda$
## An Example

Lets constrain our original function $f(x,y)=x^2+y^2$ to $g(x,y)=xy-3$
$$\begin{Bmatrix}
f_x=\lambda g_x\\
f_y=\lambda g_y\\
g=0
\end{Bmatrix}\implies \begin{Bmatrix}
2x=\lambda y\\
2y=\lambda x\\
xy=3
\end{Bmatrix}\implies \begin{Bmatrix}
2x=3\lambda/x\\
6/x=\lambda x\\
y=3/x
\end{Bmatrix}$$
$$x^2=\frac32\lambda=\frac6\lambda\therefore\lambda^2=4\therefore\lambda=\pm 2$$
For $\lambda=2$ we get the solution $y=x,xy=3\therefore(x,y)=(\sqrt3,\sqrt3)$ or $(-\sqrt3,-\sqrt3)$. For $\lambda=-2$ we have none

We dub $\lambda$ the **Lagrange multiplier**, it is what you multiply the gradient of $g$ to get the gradient of $f$ at the constraint minimum
# Proper Definition

>[!quote] The Goal
>Find the stationary points of an objective function $f(\boldsymbol{x})\in C^1$ subject to the constraint $g(\boldsymbol{x})=0$

>[!quote] The Method
>1. Define a new objective function, the **Lagrangian**
>$$L(\boldsymbol{x}\lambda)= f(\boldsymbol{x})-\lambda g(\boldsymbol{x})$$
>2. Find the **stationary points** of $L$ with respect to $\boldsymbol{x}$ and $\lambda$. This means solving $\nabla f(\boldsymbol{x})=\lambda\nabla g(\boldsymbol{x})$ and $g(\boldsymbol{x})=0$ for $\boldsymbol{x}$ and $\lambda$
>3. The constrained extrema are found in the solutions to these equations, you can then identify their nature



