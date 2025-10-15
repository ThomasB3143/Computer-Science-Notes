Section: [[Selection and Data Structures (Root)]]

A tree stored in a flat array, but can be represented as a tree (more specifically an [[AVL Trees|AVL tree]])

The tree must be **complete**. Meaning that all layers of the tree must be full, except for the bottom layer which can be filled from left to right
# Heap Properties

Max-heap:

- For every node excluding root, the value is at MOST that of its parent
- The LARGEST element is stored at the root
- In a subtree, no values are LARGER than the value stored at the subtree root

Min-heap:

- For every node excluding root, the value is at LEAST that of its parent
- The SMALLEST element is stored at the root
- In a subtree, no values are SMALLER than the value stored at the subtree root
# Array Representation

- Root at $A[1]$
- Left child of index $i$ at $A[2i]$
- Right child of index $i$ at $A[2i+1]$
- Parent of index $i$ at $A[i/2]$ (integer division)

Example:
![[Pasted image 20250422131756.png]]

| value | 22  | 13  | 10  | 8   | 7   | 6   | 2   | 4   |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- |
| index | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   |
| layer | 1   | 2   | 2   | 3   | 3   | 3   | 3   | 4   |
# Inserting

To insert into a **max-heap**, we:

1. Add the element to the rightmost free space of the bottom layer
2. If the new node is bigger than the parent, swap their positions. Set the parent node as the new node and **recursively** repeat step 2
3. Otherwise, exit

Step 2 is similar to [[Heaps#Heapify|heapify]]
# Extracting the Maximum

We often find, when implementing priority queues a need to remove the root of the heap (the largest element) like so:
## HeapExtractMax(A)
```
ret = A[1]  //returns the root
A[1] = A[HeapSize(A)]  //replaces root with leaf node
HeapSize(A) -= 1 //decrements size of heap
Heapify(A,1,HeapSize(A)) //calls heapify to restore heap
return ret //returns node that was at the root
```

Extracting the root has a running time of $O(1)$, however [[Heaps#Heapify|heapify]] has a larger complexity
# Heapify

Heapify is used to maintain the [[#Heap Properties|heap properties]] by comparing a node and its children and swapping to maintain order amongst the three nodes, then recursively calling itself upon a node to order a new trio
## Heapify(A,v,n)
```
//n is heap size
//find largest among v and 2v (left child)
largest = v
if 2v <= n and A[2v] > A[v]
	largest = 2v
if 2v+1 <= n and A[2v+1] > A[largest]
	largest = 2v+1
if largest != v
	swap A[v] and A[largest] //swap nodes to 
	Heapify(A, largest, n)
```

By calling ```Heapify(A,1,n)``` heap properties can be restored after removing the root and replacing it with a leaf node

This has $O(\log n)$ complexity
# BuildHeap

What about when we are given a completely random array and want to turn it into a heap? This function can take an array and reorder the elements such that the array has all the [[Heaps#Heap Properties|heap properties]]. It works by starting from the leaves and calling [[Heaps#Heapify|heapify]] on each
## BuildHeap(A,n)
```
for i = n down to 1
	Heapify(A,i,n)
```

It is important to note that calling this on a leaf node yields no changes.

This has a complexity of $O(n\log n)$ since $n$ [[Heaps#Heapify(A,v,n)|heapify]] calls are made and heapify has a complexity of $O(\log n)$
# HeapSort

## HeapSort(A)
```
BuildHeap(A,length(A))
for i = length(A) down to 2
	swap A[i] and A[1]
	HeapSize(A) = Heapsize(A) - 1
	Heapify(A,1,HeapSize(A))
```

1. Call [[#BuildHeap]]
2. For $i$ from the length of the array to $2$
	1. Swap $A[i]$ and $A[1]$ (the root)
	2. Decrement the heapsize to ignore the node we just swapped in any future [[#Heapify]] calls
	3. Call [[#Heapify]] on the root to restore the heap properties (whilst ignoring the nodes we've sorted)
