Section: [[Discrete Term 1 (Root)]]

Combinations are an **unordered** selection of elements from a set that allows **repeats**

Combinations of size $k$ are called k-combinations. The number of k-combinations of a set of size $n$ is $\frac{n!}{k!(n-k)!}=\binom{n}{k}$

This is a subset of size $k$
### Proposition 3.1
$$\binom{n}{k} = \binom{n}{n-k}$$
This shows us that the binomial coefficient for $n$ is symmetrical about $n/2$
### Proposition 3.2
$$\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$$
This makes sense if you check out **Pascal's Triangle**!
### Theorem 3.3 - The Binomial Theorem 
$$(a+b)^n=\sum\limits_{k=0}^{n}\binom{n}{k}a^kb^{n-k}$$
You can do calculus on this to form further equations