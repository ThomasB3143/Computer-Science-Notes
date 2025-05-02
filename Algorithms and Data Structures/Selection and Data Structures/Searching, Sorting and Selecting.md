Section: [[Selection and Data Structures (Root)]]
# Sorting

We know that no **comparison-based** sorting algorithm can beat $n\log n$, we need to look at some strategies that don't use **comparison**
## BucketSort

Suppose that the values are in the range $[0..k-1]$, start with $k$ empty buckets numbered $0$ to $k-1$. Scan the list and place element $s[i]$ in the bucket $s[i]$ and then output the buckets in order like so:

![[Pasted image 20250415142159.png]]
BucketSort(S)
```
for j = 0 to k - 1 do //initialise buckets
	b[j] = 0
end for
for i = 0 to n - 1 do //place elements in buckets
	b[S[i]] ++
end for
i = 0
for j = 0 to k - 1 do //place elements back in S
	for r = 1 to b[j] do
		S[i] = j
		i += 1
	end for
end for
```

Initialising the buckets is $O(k)$, whilst filling and emptying the buckets is $O(n)$. Combining these the time complexity will be $O(n+k)$ in the worst case

Since $k$ will likely be small compared to $n$, BucketSort is $O(n)$ in the average case

We can see that:

- If $k$ is $\omega(n\log n)$ then it is worse than merge sort
- If $k$ is $\omega(n^2)$ then it is worse than any other sorting algorithm we've looked at!

If we are not sorting numbers, then we need a [[Hash Tables#Hash Functions|hash function]] to obtain a numerical key
## RadixSort

An obvious drawback of [[Searching, Sorting and Selecting#BucketSort|BucketSort]] is that if the range of items is large, then we need a large number of buckets. To improve this we can look at one level below the item values and instead consider the decimal digits of each value. Here is the main idea:

- Have as many buckets as you have different digits (so ten for base ten)
- Repeatedly [[Searching, Sorting and Selecting#BucketSort|BucketSort]] by given digit

The number of rounds will be the greatest number of digits out of all values in the list

Consider the input 67, 23, 90, 6, 43, 22, 18, 75, 49,12, 36:

On our first pass we BucketSort using the **rightmost digit**:

| Values  | <br>90 |     | 12<br>22 | 43<br>23 |     | <br>75 | 36<br>6 | <br>67 | <br>18 | <br>49 |
| ------- | ------ | --- | -------- | -------- | --- | ------ | ------- | ------ | ------ | ------ |
| Buckets | 0      | 1   | 2        | 3        | 4   | 5      | 6       | 7      | 8      | 9      |

We now do another round on our new array 90, 22, 12, 23, 43, 75, 6, 36, 67, 18, 49. This time we consider the next digit from the right:

| Values  | <br>(0)6 | 18<br>12 | 23<br>22 | <br>36 | 29<br>43 | <br> | <br>67 | <br>75 | <br> | <br>90 |
| ------- | -------- | -------- | -------- | ------ | -------- | ---- | ------ | ------ | ---- | ------ |
| Buckets | 0        | 1        | 2        | 3      | 4        | 5    | 6      | 7      | 8    | 9      |
|         |          |          |          |        |          |      |        |        |      |        |

Dump this table and we get 6, 12, 18, 22, 23, 36, 43, 49, 67, 75, 90. This is fully sorted!!

There are $d$ bucket sort stages, where $d$ is the greatest number of digits for all values in the list, each taking $O(n)$ time. Hence the complexity of RadixSort is $O(dn)$
### Comparing RadixSort and BucketSort

Understanding that $d=\log_{10}k$ gives us $O(n\log k)$ for [[Searching, Sorting and Selecting#RadixSort|RadixSort]] and that [[Searching, Sorting and Selecting#BucketSort|BucketSort]] is $O(n+k)$ we can compare the two. Unfortunately the complexity of these once again determines on $k$ in terms of $n$:

| $k$   | RadixSort     | BucketSort | Winner? |
| ----- | ------------- | ---------- | ------- |
| $n$   | $O(n\log n )$ | $O(n)$     | Bucket  |
| $n^2$ | $O(n\log n)$  | $O(n^2)$   | Radix   |
| $2^n$ | $O(n^2)$      | $O(2^n)$   | Radix   |
| $c$   | $O(n)$        | $O(n)$     | Draw    |
# Searching

Suppose we are given $n$ **pairwise distinct** numbers in an array $A[1\dots n]$ in **sorted order**. We want to find the position $p$ of a value $x$ in $A$
## Trivial Solution

The trivial solution is simply to scan the array from left to right, stopping when we find $x$
## Binary Search

A **recursive** algorithm, binary search examines the middle-element of an array. If it is the target then we output the position. Otherwise, we **discard** the **left** or right **half** of the array if $x$ is **greater than** or **less than** the middle-element

Since $T(n)=T(n/2)+c$ we can apply the [[Recurrences#Master Theorem|master theorem]] to see that binary search is $O(\log n)$
# Selection

What if our input is **unsorted**, and we're looking for the value of the $i^{th}$ **smallest element**
## QuickSelect

QuickSelect is to **selecting** as [[Sorting#QuickSort|QuickSort]] is to [[Sorting|sorting]]. It is **recursive** and uses a **partition function** to select a pivot. However now we have only one recursive call:

- We dive into the part where we know the $i^{th}$ smallest element is to be found
- We know that, after partitioning, the pivot is in the correct position
- We can compare the pivot positioning with the sought index $i$

QuickSelect(A$[1\dots n]$, int left, int right, int i )
```
if left == right then
	return A[left]
else
	pivot = Partition(A, left, right) //returns the index of the pivot
	if i == pivot then
		return A[i]
	else if i < pivot then
		return QuickSelect(A, left, pivot - 1, i)
	else
		return QuickSelect(A, pivot + 1, right, i)
```

In the worst case, this is $O(n^2)$. This means it may actually be slower than just sorting the list. The **expected** running time of quicksort is $O(n)$
## Median-of-Median

Unlike [[Searching, Sorting and Selecting#QuickSelect|QuickSelect]], **MoM** is **doubly** recursive and has a guaranteed linear time for finding the $i^{th}$ smallest element of a sequence of unsorted items

Select(i, n)
1. Divide the $n$ elements into groups of $5$
2. Find the **median** of each group by **rote** (trivially because its still $O(1)$)
3. Recursively **Select** the median $x$ of the $n/5$ groups to be the pivot
4. Partition around the pivot $x$, let $k$ be the **rank** of $x$ (position in the sorted list)
5. If $i=k$ then return $x$
6. Else if $i<k$ then we can drop 3/10 of the elements left that are guaranteed to be greater or equal to $x$
7. Else we can drop 3/10 of the elements left that are guaranteed to be less than or equal to $x$
![[Pasted image 20250416131309.png]]
Each red rectangle is a **group**, all yellow circles are **medians** and the **pivot** $x$ is labelled. All elements in the green/blue/teal rectangle are guaranteed to be $\leq x$. We can remove them if the rank of $x$ is **less** than $i$ (as all of them will have a rank less than $i$)
![[Pasted image 20250416131623.png]]
Now the greenish-blueish rectangle is full of elements guaranteed to be $\geq x$. We can get rid of them if the rank of $x$ is **greater** than $i$, as all of them will also have a rank greater than $i$

This all means that we can remove 30% of the list every single time we recurse, removing the terrible worst-case issues of [[Searching, Sorting and Selecting#QuickSelect|QuickSelect]] 
### Complexity of MoM

Looking back on our list of operations for [[Searching, Sorting and Selecting#Median-of-Median|Select]] we can examine the complexity. Let's look at each step, assuming that Select has a time of $T(n)$
1. $O(n)$ as we are just going through the list once and dividing the list into groups of $5$
2. $O(1)$ as finding the median for $5$ elements does not scale with anything (its always five elements)
3. $T(n/5)$ as we are calling select again on the list of medians, only 1/5 of the list are now medians
4. $O(n)$ as partitioning can be done in linear time
5. Steps 5-7 are $T(7n/10)$ as we are discarding $3n/10$ elements each time guaranteed

Combining These steps we can form the relation:

$$T(n)=T(\frac n5)+T(\frac{7n}{10}+3)+n$$

We can't use [[Recurrences#Master Theorem|master theorem]] but we can use some substitution to prove that $T(k)\leq ck\;\forall\; k<n,n>0$

$T(n)\leq c(n/5)+c(7n/10+3)+n$
$\leq cn/5+3cn/4 + n$
assume $n\geq 60$
$=19cn/20+n$
$=cn-(cn/20-n)$
assume $c\geq20$
$\leq cn$
### QuickSelect or MoM

QS is singly recursive, so we have less work per layer than MoM. However it may have more layers, subject to pivot selection

We use MoM when we need **guaranteed good behaviour**

