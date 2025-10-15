Section: [[Selection and Data Structures (Root)]]

# Balanced BST

A **balanced** [[Binary Search Trees#Binary Search Trees|binary search tree]] has height of $O(\log n)$. A **degenerated** BST has height of $\Omega(n)$


We're going to find ways to keep a tree balanced when we insert or delete nodes, for the sake of avoiding the worst-case time complexities of algorithms we perform
# Rotations

Rotations are our basic **rebalancing operations**, check out this handy diagram:![[Pasted image 20250416145805.png]]
This takes $O(1)$ time, as we are modifying a constant number of parent-child links
## Trinode Reconstructing

We can combine [[AVL Trees#Rotations|rotations]] to perform a **compound operation** on a parent-child-grandchild trio. This is **trinode reconstructing**
### Single Rotation

When the child and grand-child are on the same side, we can simply rotate away from the child on the grandparent. Here we rotate left:![[Pasted image 20250416150511.png]]
### Double Rotation

When the child and grand-child are **not** on the same side, we can rotate away from the child on the middle node and away from the child on the top node like so: ![[Pasted image 20250416150835.png]]
We rotated **right** on $y$ and then **left** on $z$
# AVL Trees

An AVL tree is a self-balancing tree that adheres to one simple additional rule. For each node, the **height** of its children differ by **at most** 1. Here is a tree with the AVL property satisfied, as you can see by the labelled heights:![[Pasted image 20250416151402.png|600]]
## Insertion

When we insert something into an AVL tree, we often end up removing our height-balancing property. To amend this, we need to perform some [[AVL Trees#Rotations|rotations]] for a few specific cases. Consider the imbalanced node $a$:

| Subtree | Of child | Rotation     |
| ------- | -------- | ------------ |
| Left    | Left     | Right        |
| Right   | Right    | Left         |
| Right   | Left     | Left + Right |
| Left    | Right    | Right + Left |
Note that, in the cases where **two** rotations are performed, the first rotation is carried out on the **child**

To find all $a$, we can travel upwards from the newly inserted node and update the heights. When we encounter a node that violates the height balance property, we perform our **rotations** to fix it

This procedure can be done in $O(\log n)$ time, as trinode restructuring (time complexity $O(1)$) is done no more than once and we traverse through $\log n$ nodes
## Deletion

Where $p$ is the parent of the deleted node, there may be unbalanced nodes on the path from $p$ to the root

Let $z$ be the first unbalanced node, $y$ be the **taller** child of $z$ (not on the path), and $x$ be the **taller** child of $y$. We perform [[AVL Trees#Trinode Reconstructing|trinode reconstructing]] on $z-y-x$ 

We do need to **continue** travelling up the tree to the root, as we may have to perform multiple reconstructions along the way. With a $O(1)$ fix-up procedure, carried out at most $\log n$ times, and traversing $\log n$ nodes, we have a **time complexity** of $O(\log n)$
