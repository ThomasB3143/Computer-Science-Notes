Section: [[Discrete Term 1 (Root)]]
# Arrangements with repetitions

Recall the definition of an [[Arrangements and Permutations#Arrangements|arrangement]]

Must consider that the order of repeated elements is irrelevant when considered identical

Example: the arrangements of the letters FOOD is $\frac{4!}{2!}$

In general, this is $\frac{n!}{n_1!n_2!\dots n_r!}$ where $n$ is the size of the set where each element $i$ repeats $n_i$ times
# Combinations with repetitions

Recall the definition of a [[Combinations|combination]]

## Standard Problem #6

How many k-combinations with repetitions from $n$ objects are there where each element is chosen at least **once**?

Represent a combination as a list where repeats are adjacent like so:

A A A B C 

but insert markers between adjacent unique elements 
like so:

A A A | B | C

Hence there are $k-1$ spaces for $n-1$ markers, therefore $\binom{k-1}{n-1}$ combinations
## A Slight Change

For when each element is chosen any number of times (including zero), make a bijection between that and Standard Problem \#6 like so:

$x_1+x_2+x_3 = 7\;\;,\;\;x_i\geq0$
$y_i = x_i+1\therefore y_i\geq1\;\;,\;\;x_i=y_i-1$
$y_1-1+y_2-1+y_3-1=7\therefore y_1+y_2+y_3=10$
$\therefore \binom{k-1}{n-1}=\binom{10-1}{3-1}=\binom{9}{2}\;combinations$

So the number of k-combinations from n objects with repetition is $\binom{k+n-1}{n-1}=\binom{k+n-1}{k}$
## Extended binomial coefficients

Remember $\binom{n}{k}$ is the coefficient of $x^k$ in $(1+x)^n=\sum\limits_{k=0}^n\binom{n}{k}x^k$

But we replace $n$ with $\alpha$ because $n$ feels too much like an integer

- If $\alpha$ is a positive integer then this is just "$\alpha$ choose $k$" as it should be
- If $\alpha$ is a positive integer but $k>\alpha$, then the numerator has a factor of 0, hence $\binom{\alpha}{k}=0$ 
- If $\alpha$ is not an integer, then the numerator includes no $0$, hence $\binom{\alpha}{k}\neq 0$ and the power series $(1+x)^\alpha$ 
### Maclaurin's theorem

$\binom{\alpha}{k}=\frac{\alpha(\alpha-1)\dots(\alpha-k+1)}{k!}$ 

### Upper negation

$\binom{-n}{k}=(-1)^k\binom{k+n-1}{k}=(-1)^k\binom{k+n-1}{n-1}$

We can use this to define power series like this:
$$\frac{1}{(1+x)^n}=\sum\limits_{k=0}^n\binom{-n}{k}x^k=\sum\limits_{k=0}^n(-1)^k\binom{k+n-1}{k}x^k$$
and a special switch-up:
$$\frac{1}{(1-x)^n}=\sum\limits_{k=0}^n\binom{-n}{k}(-x)^k=\sum\limits_{k=0}^n(-1)^k\binom{k+n-1}{k}(-1)^kx^k=\sum\limits_{k=0}^n\binom{k+n-1}{k}x^k$$