Section: [[Fundamental Data Structures (root)]]
## Arrays

A sequence of elements is called an array and usually denoted $A[1],A[2],\dots,A[n]$

Elements are stored in consecutive memory cells (**contiguous**) and of the same type (**homogeneous**) with a **fixed-size**

Finding the $i^{th}$ element takes a constant unit of time. However, erasing an element requires all elements ahead to be shuffled back to fill the empty space.
## Linked Lists

-  A list is made up of nodes, with each storing an element and a link to another node
- The first node is called the **head**
- The last node is the **tail** and points to NULL
- Nodes are not contiguous

For a list $L$, we define the head and tail as $L.head$ and $L.tail$ respectively (and potentially define $L.size$)

For any node $N$, we define the element and pointer as $N.data$ and $N.next$![[Pasted image 20250409143219.png]]
Finding the $i^{th}$ element of a list requires traversing through all nodes prior to it as you can see, using pointers to travel to the next node

Inserting or deleting an element requires fixing the pointers of adjacent elements and nothing else, much more efficient than inserting into an array
![[Pasted image 20250409144501.png]]
## Doubly Linked Lists

Each node in this list stores two pointers. One to the next node and one to the precious nodes. We also have two **sentinel nodes**, a header and a trailer at the start and end of the list
![[Pasted image 20250409145433.png]]
## Circularly Linked Lists

There are no beginning or end nodes. Where the tail would point to NULL it instead points to the head. A **cursor** node is the starting node when we traverse the list
![[Pasted image 20250409150005.png]]
