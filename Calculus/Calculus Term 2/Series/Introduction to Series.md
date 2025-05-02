Section: [[Series (Root)]]

A series is the **sum** of a sequence, not the sequence itself (that is an ordered countably infinite set of numbers)
## Know Your Limits!

For a sequence to converge to a limit $L$ (so $\lim\limits_{n\rightarrow\infty}a_n=L$):

$\forall\epsilon,\exists N\in\mathbb{N}:\forall n>N,|a_n-L|<\epsilon$        
## Series Value

Far an infinite series we can define the partial sum:

$S_n=\sum\limits^n_{r=0}a_r=a_0+a1+\dots+a_n$
and the remainder:
$R_n=\sum\limits^\infty_{r=n+1}a_r=a_{n+1}+a{n+2}+\dots$

The series is convergent to a finite value $S$ if:
$\lim\limits_{n\rightarrow\infty}S_n=S$ or $\lim\limits_{n\rightarrow\infty}R_n=0$ since $R_n=S-S_n$
## Sums and Differences of Series

If the series' $\sum\limits^\infty_{n=0}a_n$ and $\sum\limits^\infty_{n=0}b_n$ converge, with respective sums $A$ and $B$ then:

$\sum\limits^\infty_{n=0}(a_n+b_n)=A+B$ and $\sum\limits^\infty_{n=0}(a_n-b_n)=A-B$
## First Test for Divergence

$\boxed{\text{If }\lim\limits_{n\rightarrow\infty}a_n\neq0\text{ then the series }\sum\limits^\infty_{n=0}a_n\text{ diverges}}$

Proof:

Suppose the series converges to some $S$ and $\lim\limits_{n\rightarrow\infty}S_n=S$ which means that, given arbitrary $\epsilon>0$, there exists some $N_\epsilon$ such that, for all $n>N_\epsilon$ , $|S_n-S|<\epsilon$

But also $|S_{n+1}-S|<\epsilon$ so we know that: 

$2\epsilon>|S_n-S|+|S_{n+1}-S|\geq|S_{n+1}-S|=|a_{n+1}|$

Well $\epsilon$ is arbitrary, so we know that for any $\epsilon^\prime>0$ there exists an $N$ such that $|a_n|<\epsilon^\prime$ for all $n>N$. This means that: 

$\lim\limits_{n\rightarrow\infty}|a_n|=0\therefore\lim\limits_{n\rightarrow\infty}a_n=0$
## Absolute Convergence Implies Convergence

$\boxed{\text{If }\sum\limits^\infty_{n=1}|a_n|\text{ converges then }\sum\limits^\infty_{n=1}a_n\text{ converges}}$  
Proof:

Let $S_n=\sum\limits^n_{r+1}a_r$ and $T_n=\sum\limits^n_{r+1}|a_r|$ . Then for each $r$ we have:

$0\leq a_r+|a_r|\leq 2|a_r|$ and $0\leq S_n+T_n\leq 2T_n$

But we know that $\lim\limits_{n\rightarrow\infty}T_n=T$ exists so:

$0\leq\lim\limits_{n\rightarrow\infty}(S_n+T_n)\leq 2T$ so the series $\lim\limits_{n\rightarrow\infty}(a_n+|a_n|)$ converges. Using the [[Introduction to Series#Sums and Differences of Series|"Difference of Convergent Series" Theorem]] we can show that:

$\sum\limits^\infty_{n=1}(a_n+|a_n|)-\sum\limits^\infty_{n=1}|a_n|=\sum\limits^\infty_{n=1}a_n$ also converges
## Comparison Test

These are fundamental rules used to prove all of our other convergence tests.
### Convergence

Let $\sum\limits^\infty_{n=1}b_n$ be a convergent series of positive terms and let $\sum\limits^\infty_{n=1}a_n$ be a series. If there exists and integer $N$ such that $\forall n>N,|a_n|\leq b_n$ then $\sum\limits^\infty_{n=1}a_n$ is an absolutely convergent series
### Divergence

Let $\sum\limits^\infty_{n=1}b_n$ be a divergent series of positive terms and let $\sum\limits^\infty_{n=1}a_n$ be a series. If there exists and integer $N$ such that $\forall n>N,0\leq b_n\leq a_n$ then $\sum\limits^\infty_{n=1}a_n$ is a divergent series
## Ratio Test

Let  $\sum\limits^\infty_{n=1}a_n$ be a series where $a_n\neq0$ and $\lim\limits_{n\rightarrow\infty}|\frac{a_{n+1}}{a_n}|=L$ 
1. If $L<1,\sum\limits^\infty_{n=1}a_n$ is an absolutely convergent series
2. If $L>1,\sum\limits^\infty_{n=1}a_n$ is a divergent series
3. if $L=1$ then the test fails
## The $n^{\text{th}}$ Root Test

Let $\sum\limits^\infty_{n=1}a_n$ be a series where $\lim\limits_{n\rightarrow\infty}\sqrt[n]{|a_n|}=L$
1. If $L<1,\sum\limits^\infty_{n=1}a_n$ is an absolutely convergent series
2. If $L>1,\sum\limits^\infty_{n=1}a_n$ is a divergent series
3. if $L=1$ then the test fails
## Alternating Series Test

The series $\sum\limits^\infty_{n=1}(-1)^{n+1}a_n$ converges if:

- $a_n>0$
- $\forall n,a_{n+1}\leq a_n$
- $\lim\limits_{n\rightarrow\infty}a_n=0$
## Subsequence Theorem

A **subsequence** is a new sequenced derived by removing some or none of the elements from the original sequence, without changing the order of elements
## Grouping and Rearranging

If a series converges, we can insert brackets/groupings without altering the sum