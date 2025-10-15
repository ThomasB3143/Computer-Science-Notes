Section: [[Asymptotic Notation and Sorting (Root)]]
# Iterative Algorithms
## InsertionSort

InsertionSort($a_1,\dots,a_n\in\mathbb{R},n\geq 2$) 
```
for j = 2 to n do
	x = a_j
	i = j - 1
	while i > 0 and a_i < x do
		a_i+1 = a_i
		i = i - 1
	end while
	a_i+1 = x
end for
```

For each $j$ it inserts the $j^{th}$ element into the already sorted sequence $a_1,\dots,a_{j-1}$. This yields a sorted $a_1,\dots,a_j$

With a running time between $n-1$ and $\frac{n(n-1)}{2}$ this has a worst case of $O(n^2)$
## SelectionSort

SelectionSort($a_1,\dots,a_n\in\mathbb{R},n\geq 2$)
```
for i = 1 to n - 1 do
	elem = a_i
	pos = i
	for j = i + 1 to n do
		if a_j < elem then
			elem = a_j 
			pos = j
		end if
	end for
	swap a_i and a_pos
end for
```

Foe each $i$ with a smaller element somewhere above, it will find the **smallest** and swap. Much like many other comparison-based algorithms, this has a worst case of $O(n^2)$
## BubbleSort

BubbleSort($a_1,\dots,a_n\in\mathbb{R},n\geq 2$)
```
for i = n to 2 do
	for j = 2 to i do
		if a_j-1 > a_j then
			swap a_j-1 and a_j
		end if
	end for
end for
```

It compares adjacent elements repeatedly to bring larger elements to the front of the list. This has a complexity of $O(n^2)$ however can be optimised by terminating when no swap is executed during the inner for-loop
# Recursive Algorithms
## MergeSort

MergeSort(list m)
```
if length(m) <= 1 then
	return m
end if
int middle = length(m)/2
list left = m[1..middle]
list right = m[middle + 1..length(m)]
return Merge(MergeSort(left),MergeSort(right))
```

We split apart the list and merge until the list consists of one or no elements (hence it is sorted). We then merge the sorted lists and return that

Merge(list A, list B)
```
list result = []
while length(A) > 0 or length(B) > 0 do
	if length(A) > 0 and length(B) > 0 then
		if A[0] <= B[0] then
			result = result + A[0]
			A = A[1..length(A)]
		else
			result = result + B[0]
			B = B[1..length(B)]
		end if
	else if length(A) > 0 then	
		result = result + A
		B = []
	else
		result = result + B
		B = []
	end if
end while
return result
```

Merging has a time complexity of $O(n)$ and must be called on a scale of $\log_2n$. Therefore the worst case of MergeSort is $O(n\log_2n)$
## QuickSort

QuickSort(list A, int left, int right)
```
if left < right then
	pivot = Partition(A, left, right)
	QuickSort(A, left, pivot - 1)
	QuickSort(A,pivot + 1, right)
end if
```

Essentially, we select a partition element and reposition the sub-list such that every element to the left of the pivot and right of the pivot is smaller and larger than the pivot. Then we call QuickSort on the new sub-lists on either side of the pivot

The complexity of QuickSort is entirely dependant on position of the pivot element once we have partitioned. In the best case, we want the pivot to be in the middle of the partitioned list. In the worst case the pivot will be the rightmost or leftmost element in the list

