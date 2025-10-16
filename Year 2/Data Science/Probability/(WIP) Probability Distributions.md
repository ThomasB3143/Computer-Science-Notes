#wip Section: [[Probability (Root)]]
# Random Variables

A random variable is a **function** which assigns a number to each outcome in the sample space of a random experiment. A **discrete random variable** is one which can take a finite number of values **or** an infinite distinguishable sequence of values.
# Probability Mass Function

The probability distribution of a random variable $X$ describes the probabilities associated with each possible outcome of $X$

For an outcome $x_k$:
$$P(X=x_k)=f(x_k)$$
Where $f$ is the **Probability Mass Function**

The value is a probability, meaning that all values are $\geq 0$ and the sum of all possible values is $1$
# Cumulative Distribution Function

The CDF for a random variable is defined as:
$$F(x)=P(X\leq x)=\sum_{x_i\leq x}P(X=x_i)=\sum_{x_i\leq x}f(x_i)$$
# Mean and Variance

## Mean

Mean is the centre or middle of the probability distribution:
$$\mu=\sum_x xf(x)$$
Denoted $E(X)$ or the **expectation**

Note that $E[X^2]$ is the **second moment**, and $E[X]$ is the **first moment**
## Variance
$$\sigma^2=\sum_x x^2f(x)-\mu^2=V(X)$$
Measures the dispersion or variability in a distribution. The variance is the **central second moment**
# Transforming Random Variables

The two laws we use to transform random variables are as follows:

1. Functions of random variables are also random variables
2. $E[h(x)]=\sum h(x_i)f(x_i)$

These give us the following properties:

- $E(aX+b)=aE(X)+b$
- $E[h(X)]=\sum_x h(x)f(x)$
- $V(aX+b)=a^2V(X)$
- $V(X)=E(X^2)-E(X)^2$
# Independence of Random Variables

For random variables that share no outcomes, we can say that:
$$V(X_1+X_2+\dots+X_n)=V(X_1)+V(X_2)+\dots+V(X_n)$$
# Linearity of Expectation

$$E(X_1+X_2+\dots+X_n)=E(X_1)+E(X_2)+\dots+E(X_n)$$
This always holds for any set of random variables
# Discrete Uniform Distribution

This assumes a finite number of possible values, each with equal probability like so:
$$X\sim Uni(n)$$
$$P(X=k)=f(x)=\frac1n$$
## Consecutive Integers

Suppose that $X$ is a discrete uniform random variable on the consecutive integers, then:
$$\mu=E[X]=\frac{b +a}{2}$$
$$\sigma^2=Var(X)=\frac{(b-a+1)^2-1}{12}$$
Like rolling a standard six-sided dice!
# Bernoulli Distribution

A Bernoulli trial is an experiment in which there are only **two** possibilities, like tossing a coin!