Section: [[Selection and Data Structures (Root)]]

A **rooted binary tree** is one where elements have at most **two children** (we'll cover what trees are in the next topic)

We dub these children the **left** child and **right** child

- One note is designated the **root node**, it has no parents and all other nodes are -**descendants**
- The **size** of a tree is the number of nodes in it
- The **depth** of a node is its distance from the root
- The depth of a **tree** is the depth of its deepest node
- A **leaf node** is a node with no children

Now we know all of this, we can get to using them for all sorts of cool things. Trees lend themselves gracefully to **recursion**, as a tree is comprised of a root node and two smaller trees
# Arithmetic Expressions

We can represent arithmetic expressions as a binary trees. Where **leaves** represent constants and variables and internal nodes are **operators** performed on its left and right subtrees. Consider the following binary tree:![[Pasted image 20250416140625.png]]

This represents into the expression:
$$((((3+1)\times3)/((9-5)+2))-((3\times(7-4))+6))$$
# Implementing Binary Trees

A binary tree can be implemented as an array, where for any index $i$ the children are stored at indexes $2i+1$ and $2i+2$.  Have a look at this example:![[Pasted image 20250416141209.png]]
We can see that we are wasting a bit of space by creating indexes for all elements in a **complete** tree
# Binary Search Trees

A binary tree with two additional requirements. For any given node $v$:

- All elements in the left sub-tree are **smaller** than $v$
- All elements in the right sub-tree are **greater** than $v$

Here is a prime example:![[Pasted image 20250416142016.png]]
## Traversing

To traverse a tree is to visit each node in the tree exactly **once**. There are **three** naturally **recursive** ways to do this:

- Preorder - the root is visited first
- Inorder - the root is visited after one sub-tree has been visited
- Postorder - the root is visited after both sub-trees have been visited
## Inserting

Inserting into a tree is quite simple, we start from the root of the tree:

- If the node is a match, return (its already in the tree)
- If the new key is smaller than that of the current node, insert on the left
- Otherwise insert on the right
## Searching

Searching follows a similar idea as [[Binary Search Trees#Inserting|inserting]], simply:

- If it is a match, return
- If we're looking for something smaller, go left
- Otherwise go right
## Deleting

Here's where it gets hard, we first need to [[Binary Search Trees#Searching|search]] for the node (the easy part)

Then we need to consider the following cases:

- If the node is a leaf, we can just remove it
- If the node has one child, we can remove it and replace it with its child
- If it has two children then we have to do a bit more work...

We can find the smallest element greater than the node we are deleting, and swap it out. Look at this tree:![[Pasted image 20250416144509.png]]
If we want to remove 3, we find the smallest node that is larger (the smallest node in the right sub-tree), which is 4. We can swap out 3 for 4 and leave it at that:
![[Pasted image 20250416144713.png]]

