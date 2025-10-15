Section: [[Probability (Root)]]

>[!cite] Definition
>Combinatorics is the study of **counting** and the **arrangement** of objects

# The Product Rule

>[!cite] Definition
>If a sequence of tasks can be done in $n_1,n_2,\dots,n_m$ ways, and each task arrives after the other, the number of ways to do one of these tasks is $n_1n_2\dots n_m$

If I have three restaurants I could go to, and each one has 5 dishes, there are 15 ways I can get food.
# The Sum Rule

>[!cite] Definition
>If a sequence of tasks can be done in $n_1,n_2,\dots,n_m$ ways, and the only condition is that no two tasks can be done simultaneously, the number of ways to do one of these tasks is $n_1+n_2+\dots+n_m$

If I have three restaurants I could go to, and each one has 5 dishes, there are 15 ways I can get food.
# Which to Use?

If the tasks are independent, [[#The Sum Rule]]. If the tasks are dependent, [[#The Product Rule]].
# Permutations

A permutation is the counting of **distinct** objects in an **ordered** arrangement. An $r$-permutation is one of $r$ elements.

When we want an $r$-permutation of $n$ elements, we use the following notation and equation:
$$P(n,r)=n(n-1)(n-2)\dots(n-r-1)=\frac{n!}{(n-r)!}$$
## Permutations With Repeats

Suppose our set has $n$ objects, where $n_1$ are of one type, $n_2$ are of another type and so on. We calculate the number of permutations like so:
$$P(n;n_1,n_2,\dots,n_k)=\frac{n!}{n_1!n_2!\dots n_k!}$$
# Combination

Similar to [[#Permutations]], a combination is the counting of distinct objects in an **unordered** arrangement. We use "$r$-combination" in the same sense:
$$C(n,r)=\binom{n}{r}=\frac{n!}{(n-r)!r!}$$
Just like the formula for permutations, but we divide by $r!$ to reduce the subsets of combinations with the same elements in different orders.
# Set Theory

You know a lot of the notation, a set is a collection of **unordered** objects.
# Theory of Probability

## Experiment

>[!cite] Definition
>A procedure yielding one of a given set of possible outcomes
## Sample Space

>[!cite] Definition
>This is the set of possible outcomes for an experiment
## Event

>[!cite] Definition
>This is a subset of the sample space


