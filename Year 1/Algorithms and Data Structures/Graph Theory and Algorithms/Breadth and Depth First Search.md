Section: [[Graph Theory and Algorithms (Root)]]
# Representing Graphs
## Adjacency List

For each vertex, we list the vertices adjacent to it, this is represented as a **list of lists**
## Adjacency Matrix

For $n$ vertices, we use an $n\times n$ matrix, where the $a_{ij}$ is a $1$ or $0$ if vertices $i$ and $j$ are neighbours or not.

This means that in a [[Introduction to ADS Graphs#Directed Graphs|directed graph]] $a_{ij}\not\equiv a_{ji}$ whilst in a non-directed graph $a_{ij}\equiv a_{ji}$ 

![[Pasted image 20250428105130.png]]
## Comparing Lists and Matrices


| Representation   | Space | Initialising | Copy  | Inserting | Listing neighbours | Determining neighbourness |
| ---------------- | ----- | ------------ | ----- | --------- | ------------------ | ------------------------- |
| Edge Array       | $m$   | $1$          | $m$   | $1$       | $m$                | $m$                       |
| Adjacency Matrix | $n^2$ | $n^2$        | $n^2$ | $1$       | $n$                | $1$                       |
| Adjacency List   | $n+m$ | $n$          | $m$   | $1$       | $n$                | $deg(u)=O(n)$             |
# Breadth-First Search

Suppose we have a graph $G=(V,E)$ and source vertex $s$, and we want to find the [[Paths, Cycles and Trees#Distance|distance]] from $s$ to every other vertex. We can perform a **breadth-first search** to do so

The **BFS** maintains a **queue** of vertices that have been discovered but not processed, it labels the vertices:

- Undiscovered
- Discovered
- Discovered and Processed

BFS also keeps an **array** $d$ where $d[s]=0$. If we discover $v$ whilst processing $u$ then we set $d[v]=d[u]+1$

The algorithm essentially works like so:

1. All vertices are **undiscovered** except for $s$, which is $discovered$. $d[s]=0$ and we add $s$ to the **queue**
2. While the queue is not empty:
	1. Remove the **first vertex** $v$ from the queue
	2. Add each **undiscovered** neighbour $u$ to the queue and mark them as **discovered**, setting $d[u]=d[v]+1$
	3. Mark $v$ **processed**
## Complexity of BFS

Lets look at the **worst-case** running time of BFS, assume it takes a constant time to test, update labels, enqueue, dequeue, etc.

Initialisation is $O(V)$, each vertex enters and leaves the queue **once** hence queue operations are $O(V)$, overall we have to examine $E$ neighbours which is $O(E)$

Thus the total run time is $O(V+E)$
## Breadth-First Tree

If we only leave edges between every processed vertex and the vertices discovered during its processing, we are left with a [[Trees and Forests|tree]] 
# Depth-First Search

**DFS** explores a graph. However, unlike [[#Breadth-First Search]] it does not find **distances** to the source, instead finding the **discovery and finish times**. Once again we have: undiscovered, discovered and processed vertices. Here is how it works:

1. Source vertex is **discovered** at time $1$, all others are **discovered**
2. Repeat
	1. Increment the time
	2. If there exists an **undiscovered neighbour** of the current vertex, mark it **discovered** and set it to the current (noting its discovery time)
	3. Otherwise mark the current vertex **processed**, note its finish time and return to its **predecessor**
	4. If it has not predecessor but we still have undiscovered vertices, jump to one. Otherwise stop, if all vertices are now processed

Note that step 4 aims to process all vertices, even if some are not [[Paths, Cycles and Trees#Connectivity|connected]] to the source
## Complexity of DFS

Initialisation takes $O(V)$ time, we also spend $O(V)$ time incrementing the time, colouring vertices and updating $d$ and $f$

We consider each neighbour of every vertex at most once, taking time $O(E)$

Overall, the total time is $O(V+E)$
## Depth-First Tree

Similar to the [[#Breadth-First Tree]], following the edges between vertices and their **predecessors** will form a **depth-first tree**