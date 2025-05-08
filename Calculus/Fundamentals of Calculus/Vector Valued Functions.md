Section: [[Fundamentals of Calculus (Root)]]

Throughout previous sections, we have been dealing with **real valued functions**, ones which output a real number. A **vector valued function** outputs a list of numbers in the form of a **vector**
# Jacobian Matrix

Suppose we have a function $f:\mathbb{R}^n\mapsto\mathbb{R}^m$ where $f=(f_1(x),f_2(x),\dots,f_m(x))$. Form a matrix $J$ where $J_{ij}=\frac{\delta f_i}{\delta x_j}$. The resulting matrix of partial derivatives is called the **Jacobian Matrix**
$$J=\begin{pmatrix}
\frac{\delta f_1}{\delta x_1}&\cdots&\frac{\delta f_1}{\delta x_n}\\
\vdots&\ddots&\vdots\\
\frac{\delta f_m}{\delta x_1}&\cdots&\frac{\delta f_m}{\delta x_n}
\end{pmatrix}$$
# Compound Functions

>[!quote] Theorem
>For functions $f:A\mapsto B$ and $g:B\mapsto C$, we know that:
>$$J_{g\cdot f}=J_gJ_f$$

This is **chain rule!**
# Linear Approximations

We can use the **Jacobian matrix** to form linear approximations of a multivariate function at a point:
$$f(\boldsymbol{x}+h\boldsymbol{v})\approx f(\boldsymbol{x})+J_f(\boldsymbol{x})(h\boldsymbol{v})$$
- $\boldsymbol{x},\boldsymbol{v},h\boldsymbol{v}$ are all $n$-dimensional vectors
- $J_f(\boldsymbol{x})$ is an $m\times n$ matrix
- $f(\boldsymbol{x}),J_f(\boldsymbol{x})(h\boldsymbol{v})$  are $m$-dimensional vectors

Lets look at an example on $g:\mathbb{R}^2\mapsto\mathbb{R}^2=(\sin(x_1+x_2),\cos(x_1-x_2))$

$$J_g=\begin{pmatrix}
\cos(x_1+x_2)&\cos(x_1+x_2)\\
-\sin(x_1-x_2)&\sin(x_1-x_2)
\end{pmatrix}$$
$$J_g\left(\frac{3\pi}{4},\frac{\pi}{4}\right)=\begin{pmatrix}
\frac{\delta g_1}{\delta x_1}&\frac{\delta g_1}{\delta x_2}\\
\frac{\delta g_2}{\delta x_1}&\frac{\delta g_2}{\delta x_2}
\end{pmatrix}=\begin{pmatrix}
\cos(\pi)&\cos(\pi)\\
-\sin(\pi/2)&\sin(\pi/2)
\end{pmatrix}=\begin{pmatrix}
-1&-1\\
-1&1
\end{pmatrix}$$

So near $\left(\frac{3\pi}{4},\frac{\pi}{4}\right)$ we can approximate $g$ by:

$$g\left(\frac{3\pi}{4}+\delta_x,\frac{\pi}{4}+\delta_y\right)=g\left(\frac{3\pi}{4},\frac{\pi}{4}\right)+\begin{pmatrix}
-1&-1\\
-1&1
\end{pmatrix}\begin{pmatrix}
\delta_x\\
\delta_y
\end{pmatrix}=\begin{pmatrix}
0\\0
\end{pmatrix}+\begin{pmatrix}
-\delta_x-\delta_y\\
-\delta_x+\delta_y
\end{pmatrix}$$
