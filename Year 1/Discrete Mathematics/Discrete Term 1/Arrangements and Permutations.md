Section: [[Discrete Term 1 (Root)]]
# Arrangements

Arrangements are a **finite** sequence of items with relevant **order**

Arrangements of a size $k$ on $n$ choices is $n^k$, but finding arrangements **without** repeats requires a new definition...
## Multiplication Principle

When we have an arrangement of length $k$ where there are $n_i$ choices for the $i^{th}$ item, there are a total of $n_1n_2n_3\dots n_k$ possible arrangements
# Permutations

Permutations are an **arrangement** of a set, using **each** element once

Permutations of a set of size $n$ is $n!$

An r-permutation is an arrangement of \(r\) distinct elements from a set
$P(n,r) = \frac{n!}{(n-r)!}$
# Counting examples
## Additive Principle

Where A and B are two finite disjoint sets $A\cap B = \emptyset$, the cardinality of the union is the sum of the individual cardinalities

Note that we use the [[#Additive Principle]] when considering mutually exclusive events that both satisfy a condition. However, we use the [[#Multiplication Principle]] when considering the simultaneous existence of multiple choices