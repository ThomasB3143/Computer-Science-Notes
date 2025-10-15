Section: [[Calculus Term 2 (Root)]]

Recall that the [[Power Series#Taylor Series|Taylor Series]] method aims to represent an **infinitely differentiable** function as an infinite [[Power Series]] like so:
$$f(x)=\sum^{\infty}_{n=0}f^{(n)}(x_0)\frac{(x-x_0)^n}{n!}$$
Which converges to $f(x)$ on $(x_0-r,x_0+r)$, where $r$ is the [[Power Series#Radius of Convergence|radius of convergence]]

This is great, but we require $f(x)$ to be **smooth** at $f(x_0)$
# A New Series Expansion

We can use a new expansion using **trigonometric functions** by expressing a function as an infinite sum of sines and cosines such that the series converges to the function value at *almost* any point
## Key Facts

1. $$\int^{\pi}_{-\pi}\cos mx\;dx=\int^{\pi}_{-\pi}\sin  mx\;dx=0$$
2. $$\sin(A+B)=\sin A\cos B+\cos A\sin B$$
3. $$\sin(A-B)=\sin A\cos B-\cos A\sin B$$

From this we can derive the following:
$$\sin A\cos B=\frac12(\sin(A-B)+\sin(A+B))$$
$$\int^{\pi}_{-\pi}\sin nx\cos mx\;dx=\frac12\int^{\pi}_{-\pi}\sin  (n-m)x\;dx+\frac12\int^{\pi}_{-\pi}\sin  (n+m)x\;dx=0$$
## Constructing the Series

Lets construct a new series to approximate $f(x),-\pi<x<\pi$:$$f(x)\approx\frac{a_0}{2}+\sum^{\infty}_{n=1}a_n\cos nx+b_n\sin nx$$The range is not a real restriction, as we can always scale our function $f(x),a<x<b$ by setting:
$$f(x)=g\left(\left(x-\frac{b+a}{2}\right)\frac{2\pi}{b-a}\right)$$
Where $g$ is a function on $(-\pi,\pi)$
## Fourier Coefficients

Assuming our previous series exists, we can **integrate** and multiply by $\cos mx$ to get:
$$\int^{\pi}_{-\pi}f(x)\cos mx\;dx\approx\int^{\pi}_{-\pi}\left(\frac{a_0}{2}+\sum^{\infty}_{n=1}a_n\cos nx+b_n\sin nx\right)\cos mx\;dx$$$$=\frac{a_0}{2}\int^{\pi}_{-\pi}\cos mx\;dx+\sum^{\infty}_{n=1}a_n\int^{\pi}_{-\pi}\cos nx\cos mx\;dx+\sum^{\infty}_{n=1}b_n\int^{\pi}_{-\pi}\sin nx\cos mx\;dx$$
Only one term of $\cos nx\cos mx$ is non-zero, when $n=m$ and $\cos nx\cos mx=\pi$. Therefore:
$$=\pi a_m$$We can also integrate then multiply by $\sin mx$ instead:
$$\int^{\pi}_{-\pi}f(x)\sin mx\;dx\approx\int^{\pi}_{-\pi}\left(\frac{a_0}{2}+\sum^{\infty}_{n=1}a_n\cos nx+b_n\sin nx\right)\sin mx\;dx$$$$=\frac{a_0}{2}\int^{\pi}_{-\pi}\sin mx\;dx+\sum^{\infty}_{n=1}a_n\int^{\pi}_{-\pi}\cos nx\sin mx\;dx+\sum^{\infty}_{n=1}b_n\int^{\pi}_{-\pi}\sin nx\sin mx\;dx$$
$$=\pi b_m$$
# The Fourier Series

For a function $f(x),-\pi<x<\pi$, the Fourier series is:
$$f(x)\approx\frac{a_0}{2}+\sum^{\infty}_{n=1}a_n\cos nx+b_n\sin nx$$
Where (using our previous rearrangements):
$$a_n=\frac1\pi\int^{\pi}_{-\pi}f(x)\cos nx\;dx\;\;,\;\;b_n=\frac1\pi\int^{\pi}_{-\pi}f(x)\sin nx\;dx$$

>[!quote] Theorem
>If $f$ is piecewise continuous and $\int^{\pi}_{-\pi}[f(x)]^2\;dx$ exists, then the Fourier series [[Introduction to Series#Convergence|converges]]
>- For all **continuous** points, the series converges to $f(x)$
>- For points $x_0$ with discontinuity, the series converges to$$\frac{1}{2}\left(\lim_{x\rightarrow x_0^-}f(x)+\lim_{x\rightarrow x_0^+}f(x)\right)$$
