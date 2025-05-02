Section: [[Graph Theory and Algorithms (Root)]]

Suppose we have a graph with a **weight** or **cost** for each edge. There are often times where we want to find the subset of edges that keeps the graph [[Paths, Cycles and Trees#Connectivity|connected]] with the **lowest overall cost**. This is always a [[Trees and Forests#Spanning Trees|spanning tree]], as to have a [[Paths, Cycles and Trees#Cycle|cycle]] means there exists an edge which can be removed whilst remaining connected. The **minimum spanning tree** must have the following properties:

- $|V|-1$ edges
- No cycles
- Not necessarily unique

We can represent a [[Introduction to ADS Graphs#Weighted Graphs|weighted graph]] as an [[Breadth and Depth First Search#Adjacency Matrix|adjacency matrix]] where a $0$ in $a_{ij}$ means **no** edge, and a $w$ means an edge of weight $w$ between $i$ and $j$

# Kruskal's Algorithm

1. Sort the edges by weight
2. Starting from the edge of lowest weight, add the edge to an initially empty subset if its addition will not create a **cycle**

This has a running time of $O(E\log V)$
# Prim's Algorithm

1. Let $U=\lbrace u\rbrace$ where $u$ is some randomly chosen vertex
2. Let $A=\emptyset$
3. Until $U$ contains all vertices:
	1. Find the least weighing edge $e$ that joins a vertex between $U$ and $V\setminus U$
	2. Add $e$ to $A$ and the vertex from $V\setminus U$ to $U$

This has a running time of $O(V\log V + E)$
# Generic MST Algorithm

Both [[#Kruskal's Algorithm]] and [[#Prim's Algorithm]] are **greedy** algorithms, as they only consider the locally optimal choice at each step and slowly build $A$ such that it is always a **subset** of some MST. A generic MST follows the definitions:

- Let $A$ be a subset of an MST, if $A\cup \lbrace(u,v)\rbrace$ is also a subset of an MST then $(u,v)$ is a **safe** edge for $A$
- A **cut** $(S,V-S)$ of a graph is a partition of $V$
- An edge **crosses** a cut if its [[Introduction to ADS Graphs#Endpoints|endpoints]] are each in $S$ and $V-S$
- The **light edge** is the smallest weighted edge **crossing** a cut
- A cut **respects** a set of edges if no edge **crosses** the cut
##### GenericMST(G,w)
```
A = {}
while A is not a spanning tree
	find an edge that is safe for A
	add the edge to A
return A
```

>[!quote] Theorem
>For a connected, undirected, weighted graph $G=(V,E)$ let $A\subseteq E$, where $A$ is a subset of some MST. Let $(S,V-S)$ be some **cut** of $G$ that respects $A$ and let $(u,v)$ be a **light edge** crossing $(S,V-S)$. Then the edge is **safe** for $A$
>
