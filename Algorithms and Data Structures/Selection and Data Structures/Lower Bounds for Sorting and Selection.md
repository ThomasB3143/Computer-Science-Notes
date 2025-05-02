Section: [[Selection and Data Structures (Root)]]
# Decision Trees

A decision tree is a **full** [[Binary Search Trees#|binary tree]] (each node has **zero** or **two** children). This can be used to represent the comparisons made by algorithms ran on a given input

- **Internal nodes** (those with children) are labelled " $i:j$ ", meaning elements at indices $i$ and $j$ (with respect to original order) are compared
- **Downward edges** are labelled " $\leq$ " or " $>$ " or something other, subject to the outcome of comparisons
- **Leaves** are labelled with some permutation of the list, representing a possible output. We have at least $n!$ leaves, **one for each possible outcome** 
- **Branches** describe a sequence of comparisons that end in some resulting order

Here is a great example for [[Sorting#SelectionSort|SelectionSort]] on **three** elements:
![[Pasted image 20250423115936.png]]
It is plain to see (hopefully) that any **correct** sorting algorithm must be able to produce each permutation of input, hence there must be a **leaf** for each permutation

It is *slightly* less plain to see that the **longest** path from root to leaf will represent the [[Asymptotic Notation#Worst-Case Time Complexity|worst-case]] number of comparisons for a given $n$. We can actually use this to prove the following:

>[!quote] Theorem
>Any comparison-based sorting algorithm requires $\Omega(n\log n)$ comparisons in the **worst** case

**Proof**:

- Consider a tree with height $h$ and $\ell$ leaves, representing sorting $n$ elements
- Each of the $n!$ permutations appear as some leaf, so $n!\leq\ell$
- A binary tree of height $h$ has **at most** $2^h$ leaves, so $\ell\leq 2^h$
- Therefore $n!\leq 2^h$
- Now $h\geq\log(n!)$ and is now $\Omega(n\log n)$
# Adversaries

An **adversary** is a second algorithm intercepting access to the input. It provides answers that ensure the original algorithm does **not** have enough info to make a decision for **as long as possible**

Essentially, to get a good **lower bound** we must design a good adversary
## Finding the Max

Suppose we want to find the max element in an unsorted array:

> [!quote] Theorem
> Any **comparison-based** algorithm for this problem will require at least $n-1$ comparisons in the **worst case**

**Proof:**

- After $\leq n-2$ comparisons, $\geq 2$ elements never lost a comparison
- The adversary can make any of them the max and be consistent
- So the algorithm cannot make a decision as to which one is the greatest
- Hence the algorithm must make at **least** $n-1$ comparisons

The algorithm only needs to know how many elements have lost a comparison. Once $n-1$ elements have lost, the algorithm knows that the max is the one that **never lost**

Now assume each index has the status $N$ or $L$ for "never lost" or "lost" respectively. We start with $N$ for all indexes

The adversary wants to delay the change from $N\rightarrow L$

Here is a table representing the outcome and effects of comparisons, where we provide **bits** of new info and change states: 

| Status of $i$ and $j$ | Adversary's response | New status | New info |
| --------------------- | -------------------- | ---------- | -------- |
| $N:N$                 | $a_i>a_j$            | $N:L$      | 1        |
| $N:L$                 | $a_i>a_j$            | No change  | 0        |
| $L:N$                 | $a_i<a_j$            | No change  | 0        |
| $L:L$                 | Consistent           | No change  | 0        |
Since there is only **at most one** bit of info given per comparison, and $n-1$ bits are needed, we need **at least** $n-1$ comparisons
## Finding 2nd Largest

> [!quote] Theorem
> Any **comparison-based** algorithm for this problem will require at least $n+\lceil\log_2n\rceil-2$ comparisons in the **worst case

Any correct algorithm must also [[Lower Bounds for Sorting and Selection#Finding the Max|determine the max]], hence $n-1$ elements must lose at least one comparison. The second largest must also **lose to the max directly**

If the max had direct comparisons with $m$ elements, then $m-1$ of these elements must lose $2$ comparisons. Hence $n-1+m-1=n+m-2$ comparisons are needed

We can prove that the adversary can **force** $\lceil\log_2n\rceil$ comparisons involving the max like so:

We assign weights $w_i=1$ to each element $a_i$ and update them using the following rules:

| Weights     | Adversary's response | Update                    |
| ----------- | -------------------- | ------------------------- |
| $w_i>w_j$   | $a_i>a_j$            | $w_i=w_i+w_j\;\;,\;w_j=0$ |
| $w_i<w_j$   | $a_i<a_j$            | $w_j=w_i+w_j\;\;,\;w_i=0$ |
| $w_i=w_j>0$ | $a_i>a_j$            | $w_i=w_i+w_j\;\;,\;w_j=0$ |
| $w_i=w_j=0$ | Consistent           | No change                 |
From this we can deduce the following:

- $w_i=0\iff i$ has lost at least one comparison
- Weight of an element will at most double after comparison
- If the max is involved in $m$ comparisons, its wright is $\leq2^m$
- In the end, the max accumulates all the weight, so $n\leq 2^m$
- Now $\log_2n\leq m$
- This means the adversary can force $\lceil\log_2n\rceil$ comparisons with the max, proving the theorem

The algorithm to match this lower bound will find the maximum, and the find the maximum amongst those that lost directly to the overall maximum
## Finding kth largest

Let $V(n,k)$ be the number of comparisons needed to find the $k^{th}$ largest element in an array of size $n$

>[!quote] Theorem
>For all $1\leq k\leq b$, it holds that $V(n,k)\geq n-k+\lceil\log_2\binom{n}{k-1}\rceil$

This looks very hard to prove. Thankfully, this is where the lecture slides end 𓆏