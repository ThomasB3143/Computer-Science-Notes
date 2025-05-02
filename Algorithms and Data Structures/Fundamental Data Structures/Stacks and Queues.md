Section: [[Fundamental Data Structures (root)]]
## Stacks

A stack is a collection of objects inserted and removed according to the last-in-first-out (LIFO) principle. Only the most recently inserted object can be removed at any time

It may have the following methods:

- $push(e)$ - inserts element $e$ at the top of the stack
- $pop$
	- removes and returns the top element of the stack
	- returns an error if empty
- $size$ - returns the number of elements in the stack
- $isEmpty$ - returns a Boolean showing if the stack is empty
- $top$
	- returns the top element of the stack without removing
	- returns an error if empty
### Stacks as Arrays

We can implement a stack as an array by including an integer variable that points to the top of the stack

This is time efficient, as the time taken by all methods does not depend on the size of the stack.

However, using an array of fixed size can waste memory and allow overflow errors
## Queues

A queue is a collection of objects inserted and removed according to a first-in-first-out (FIFO) principle

Element access and deletion is restricted to the first element in the queue (the **front**). Element insertion is restricted to the end of the sequence (the **rear**)

It may have the following methods:

- $enqueue(e)$ - Inserts element $e$ at the **rear** of the queue
- $dequeue$ - Removes and returns the element from the front, returning an error if the queue is empty
- $size$ - returns the number of elements in the queue
- $isEmpty$ - returns a Boolean indicating if the queue is empty
- $front$ - returns the front element of the queue without removing it. An error is returned if the queue is empty
## Queues as Arrays

We can implement a queue as an array using a **circular queue**, where we define integer variables $f$ and $r$:

- $f$ is an index to a cell storing the front of the queue
- $r$ is an index to the next available cell in the queue (the after the rear if the queue isn't empty)
- the queue is empty when $f=r$
- $f=r=0$ when we initialise an empty queue
- enqueuing increments $r$
- dequeuing increments $f$

We use modulo arithmetic to let the pointers wrap around the end and start of the array. Let's look at the following methods for an array of size $N$:

- $size$ - returns $(r-f)\mod N$   
- $isEmpty$ - returns $(f==r)$
- $front$ - returns $Q[f]$ or an error if the queue is empty
- $enqueue(e)$ - $Q[r]\leftarrow e$ and $r\leftarrow r+1\mod N$ unless the list is already full
- $dequeue$ - return $Q[f]$, $Q[f]\leftarrow NULL$ and $f\leftarrow f+1\mod N$ unless the list is empty

All methods run in constant time however we are limited by the size of the array