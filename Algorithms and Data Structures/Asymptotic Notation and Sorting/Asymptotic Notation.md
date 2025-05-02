Section: [[Asymptotic Notation and Sorting (Root)]]
# Complexity
## Time Complexity
The **time complexity** of an algorithm can be expressed in terms of the number of basic operations (addition, comparison, swapping etc) used by the algorithm with an input of particular **size**
## Space Complexity

The **space complexity** of an algorithm can be expressed in terms of the memory required by the algorithm with an input of particular **size**
## Average-Case Analysis

This is interested in the **average** number of operations over all inputs of a given size
## Worst-Case Time Complexity

The **worst-case time complexity** of an algorithm can be expressed in terms of the **largest** number of basic operations used by the algorithm with an input of particular size

This can tell us how many operations we need to **guarantee** a solution, thus is a standard way to estimate the efficiency of algorithms. This is often what we use when referring to [[Asymptotic Notation#Time Complexity|time complexity]]
# Asymptotic Notation

Let's introduce some mathematical notation to compare the time complexity of functions
## Big-O Notation

It is difficult to compute the exact number of operations. Thankfully, it is often enough to just give bounds and **estimate** the number

The bounds should allow us to examine the relationship between the **number of operations** and **input size**
![[Pasted image 20250410151343.png]]![[Pasted image 20250410155025.png]]
Let $f$ and $g$ be functions from the set of integers or the set of real numbers to the set of real numbers. We say that $f$ is $O(g)$ or "$f$ is big-O of $g$" if there are constants $C$ and $k$ such that:

$|f(x)|\leq C|g(x)|\;\forall\; x\geq k$

Note that when concerned with [[Asymptotic Notation#Time Complexity|time complexity]] functions, we don't need the absolute parts (time for an algorithm can't be negative)

In this definition, we are saying that (beyond the lower bound of $k$) the absolute value of $f(x)$ is bounded from above by $C$ times the absolute value of $g(x)$

We refer to $C$ and $k$ as **witnesses** to the relationship $f(x)$ is $O(g(x))$

Note that if $C$ and $k$ are witnesses, then so are all $C^\prime$ and $k^\prime$ where $C\leq C^\prime$ and $k\leq k^\prime$

Example - Prove that $f(x)=3x^3-7x^2-4x+2$ is $O(x^3)$

For $x\geq 1$ we know $1\leq x\leq x^2\leq x^3$, hence

$|f(x)|=|3x^3-7x^2-4x+2|\leq 3x^3+7x^2+4x+2$
$\leq 3x^3+7x^3+4x^3+2x^3=16x^3$ 

hence with $k=1$ and $C=16$ as our witnesses, we have $|f(x)|\leq C|x^3|$ for all $x\geq k$

Example - Prove that $f(x)=3^x$ is NOT $O(2^x)$

Assume it is, then there exists $k$ and $C$ such that:

$3^x\leq C\times 2^x$ for all $x\geq k$, so $\left(\frac32\right)^x\leq C$

This exponential function will grow monotonically, hence no value of $C$ can remain above it for all $x\geq k$

The contradiction proves that $3^x$ is not $O(2^x)$
## Sum and Product Rules

### Sum Rule

Theorem: 

If $f_1(x)$ is $O(g_1(x))$ and $f_2(x)$ is $O(g_2(x))$ then $f_1(x)+f_2(x)$ is $O(\max\{|g_1(x)|,|g_2(x)|\})$

Proof:

Let $C_i$ and $k_i$ be witness pairs for $f_i(x)$ is $O(g_i(x))$ for $i=1,2$
Let $k=\max\{k_1,k_2\}$ and $C=C_1+C_2$. Then for $x>k$ we have:

$|f_1(x)+f_2(x)| \leq |f_1(x)|+|f_2(x)|\leq C_1|g_1(x)|+C_2|g_2(x)|\leq C\max\{|g_1(x)|,|g_2(x)|\}$
### Product Rule

Theorem: 

If $f_1(x)$ is $O(g_1(x))$ and $f_2(x)$ is $O(g_2(x))$ then $f_1(x)f_2(x)$ is $O(g_1(x)g_2(x))$

Proof:

Let $C_i$ and $k_i$ be witness pairs for $f_i(x)$ is $O(g_i(x))$ for $i=1,2$
Let $k=\max\{k_1,k_2\}$ and $C=C_1C_2$. Then for $x>k$ we have:

$|f_1(x)+f_2(x)| \leq |f_1(x)|+|f_2(x)|\leq C_1|g_1(x)|C_2|g_2(x)|= C|g_1(x)g_2(x)|$
## Big-Omega Notation

We use [[Asymptotic Notation#Big-O Notation|Big-O notation]] to find reasonable **upper bounds** for growth rates. But this doesn't help if we want a function to **match** the growth rate

To get further towards this, we need to introduce Big-O's counterpart, **Big-Omega notation**

let $f(x)$ and $g(x)$ be the functions from the set of real numbers to the set of real numbers. We can say that $f(x)$ is $\Omega(g(x))$ if there exists positive constants $C$ and $k$ such that:

$|f(x)|\geq C|g(x)|\;\forall\; x>k$ 

See how this is similar to [[Asymptotic Notation#Big-O Notation|Big-O]] just with a reversed inequality? This means that: $f(x)$ is $\Omega(g(x))\iff g(x)$ is $O(f(x))$
## Same Order Growth Rates

If $f(x)$ is both $O(g(x))$ **and** $\Omega(g(x))$ then it is $\Theta(g(x))$

This shows that it has the same order of growth rate as $g(x)$. Here are some examples to show this:

| $f(x)$    | $g(x)$     |
| --------- | ---------- |
| $x^2$     | $x^2+1$    |
| $2^x+x^2$ | $2^x+3x^4$ |
## Little-O Notation 

This is used to show when a function has a **smaller** order of growth than another

Let $f(x)$ and $g(x)$ be functions from the set of real numbers to the set of real numbers. We say that $f(x)$ is $o(g(x))$ when:

$\lim\limits_{x\rightarrow\infty}\frac{f(x)}{g(x)}=0$  

or...

$f(x)<C\times g(x)\;\forall\; x\geq k$ for witnesses $C$ and $k$ 

The second definition clearly shows that $f(x)$ is $o(g(x))\implies f(x)$ is $O(g(x))$ and $f(x)$ is NOT $O(g(x))\implies f(x)$ is NOT $o(g(x))$
#### Sublinear Functions

A function $f$ is **sublinear** when $f(x)$ is $o(x)$ so $\lim\limits_{x\rightarrow\infty}\frac{f(x)}{x}=0$
### Little-Omega Notation

$\omega$ is to $o$ what $\Omega$ is to $O$

$f$ is $\omega(g)\iff g$ is $o(f)$ 

$f(x)>C\times g(x)\;\forall\; x\geq k$ for witnesses $C$ and $k$ 
## General Rules

![[Pasted image 20250410163917.png]]
We also know the following theorems:

- If $f_1$ is $o(g(x))$ and $f_2$ is $o(g(x))$ then $f_1(x)+f_2(x)$ is $o(g(x))$ 
- If $f_1$ is $O(g(x))$ and $f_2$ is $o(g(x))$ then $f_1(x)+f_2(x)$ is $O(g(x))$
- If $f_1$ is $\Theta(g(x))$ and $f_2$ is $o(g(x))$ then $f_1(x)+f_2(x)$ is $\Theta(g(x))$ 