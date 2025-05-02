Section: [[Discrete Term 1 (Root)]]

When terms of a sequence are defined by other terms in the sequence. Popular examples include those such as $f_n=f_{n-1}+f_{n-2}$ (the Fibonacci sequence)

Recurrence relations are very well suited to proof by induction

Example - with an initial condition $t_1=1$ prove that if $t_n=2t_{n-1}+1,n\geq2$ then $t_n=2^n-1,n\geq1$

$n=1,t_1=2^1-1=1$

We have proved our base case, now assuming that the formula holds for $n$, we will try and prove it holds for $n+1$

$t_{n+1}=2t_n+1=2(2^n-1)+1=2^{n+1}-2+1$
$\therefore t_{n+1}=2^{n+1}-1$

$\therefore$ The statement holds for $t_{n+1}$, provided it does for $t_n$

If the statement holds for $t_1$, then it holds for all $t_n$, where $n\geq1$
## A General method

Let $a_n$ be a sequence with initial conditions for $a_0,a_1...a_e$ and a recurrence relation like so:

$a_n=\sum\limits_{i=1}^rc_ia_{n-i}=c_1a_{n-1}+c_2a_{n-2}+\dots+c_ra_{n-r}$

where all $c$ are specific constants. This is linear because no term has more than one factor of each $a_i$. It is homogeneous because every term involves an $a_i$ (we will look at inhomogeneous parts [[Recurrence Relations#Inhomogeneous relations|later]])

Anyway, now we seek solutions to the relation of the form $a_n=x^n$, which is:

$x^n=\sum\limits_{i=1}^rc_ix^{n-i}\therefore x^r-\sum\limits_{i=1}^rc_ix^{r-i}=0$

We divided by $x^{n-r}$ to get rid of excess powers. This is the **characteristic equation**

Now we find the roots of the characteristic equation $alpha_1,\dots,\alpha_r$. The **general solution** to the recurrence relation is:

$g(n)=a_n=d_1a_1^n+d_2a_2^n+\dots+d_ra_r^n$

Use the initial conditions to get $r$ linear equations and unknowns, solve to find all $d_i$. Then you have the solution to $a_n$

Example - Solve $a_n=3a_{n-1}+4a_{n-2},n\geq2,a_0=1,a_1=0$

Characteristic equation:

$x^n=3x^{n-1}+4x^{n-2}\therefore x^2-3x-4=0\therefore x=4,-1$
$g(n)=a_n=d_1(-1)^n+d_24^n$
$a_0=1=d_1+d_2,a_1=0=-d_1+4d_2$
$1=5d_2\therefore d_2=\frac{1}{5},d_1=1-\frac{1}{5}=\frac{4}{5}$
$\therefore a_n=\frac{4}{5}(-1)^n+\frac{1}{5}(4)^n$
### Repeated Roots

if $\alpha_1=\alpha_2=\dots=\alpha_k$ then, instead of: 

$d_1a_1^n+\dots d_ka_k^n$

we use: 

$(e_1+e_2n+\dots e_kn^{k-1})\alpha^n$
## Inhomogeneous relations

Uh oh! now $a_n=c_1a_{n-1}+\dots+c_ra_{n-r}+f(n)$ where $f(n)$ is an **inhomogeneous part**. Here are the steps to solve:
### Step 1

outline the homogeneous problem $a_n=c_1a_{n-1}+\dots+c_ra_{n-r}$ and get it into the form $a_n=d_1\alpha_1^n+d_2\alpha_2+\dots+d_r\alpha_r^n=g(n)$
### Step 2

find a solution to the full inhomogeneous problem $a_n=p(n)$ by looking at the form of $f$ and use these rules to find the form of $p(n)$:

- $f(n)=A\rightarrow p(n)=B_0$
- $f(n)=An\rightarrow p(n)=B_0+B_1n$
- $f(n)=An^2\rightarrow p(n)=B_0+B_1n+B_2n^2$
- $f(n)=Aq^n\rightarrow p(n)=B_0q^n$
- $f(n)=Anq^n\rightarrow p(n)=(B_0+B_1n)q^n$

If $f(n)$ is a sum of these, then $p(n)$ is the corresponding sum of these.
### Weird exceptions

If $f(n)$ contains $q^n$ where $q$ is repeated roof of the characteristic equation, then the homogeneous part of the solution already contains a term. In this case, replace $q^n$ with $nq^n$ or $n^kq^n$ in the case of a root repeated $k$ times

If $1$ is a root of the characteristic equation then any $f(n)=An^k=An^k1^n$ which takes us back to the first case. In this scenario, increase the powers of $n$ in the choice of $p(n)$ to fix it

Example - solve $a_n=a_{n-1}+2a_{n-2}-2n,n\geq2,a_0=a_1=0$

first we solve $a_n=a_{n-1}+2a_{n-2}$ using $a_n=x^n$

$x^n=x^{n-1}+2x^{n-2}\therefore x^2-x-2=0=(x-2)(x+1)\therefore x=2,-1$
$g(n)=d_1(-1)^n+d_22^n$

$f(n)$ is in the form $An$ therefore $p(n)$ will be in the form $B_0+B_1n$

Setting $a_n=p(n)$ we use our initial recurrence relation to get:

$B_0+B_1n=B_0+B_1(n-1)+2B_0+2B_1(n-2)-2n$
$B_0+B_1n=B_0+B_1n-B_1+2B_0+2B_1n-4B_1-2n$
$0=-B_1+2B_0+2B_1n-4B_1-2n=(-5B_1+2B_0)+(2B_1-2)n$
$\therefore-5B_1+2B_0=0\;\;,\;\;2B_1-2=0\therefore B_1=1\therefore B_0=\frac{5}{2}$
$\therefore p(n)=n+\frac52$
$a(n)=g(n)+p(n)=d_1(-1)^n+d_22^n+n+\frac52$

NOW we can find the $d_i$ constants using the initial conditions $a_0=a_1=0$

$a_0=0=d_1+d_2+\frac52\therefore d_1+d_2=-\frac52$
$a_1=0=-d_1+2d_2+\frac72\therefore-d_1+2d_2=-\frac72$
$\therefore 3d_2=-6\therefore d_2=-2\therefore d_1=-\frac52+2=-\frac12$

so FINALLY $a(n)=-\frac12(-1)^n-2(2)^n+n+\frac52$