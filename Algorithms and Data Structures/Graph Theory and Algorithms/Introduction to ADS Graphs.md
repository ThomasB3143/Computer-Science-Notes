Section: [[Graph Theory and Algorithms (Root)]]

I don't want to link the file because it'll mess up my graph, but just read "Introduction to Graphs" in the "Discrete Mathematics/DiscreteTerm 2" folder

>[!quote] Graph - Definition
>A graph $G$ is a pair $V(G),E(G)$, where $V(G)$ is a **nonempty** set of **vertices** and $E(G)$ is a set of **unordered** pairs of vertices from $V(G)$ called **edges**

We often just call the sets $V$ and $E$ when context provides the $G$ we are talking about
## Important Terminology
##### Endpoints
$u$ and $v$ are the **endpoints** of the edge $uv$
##### Neighbours
Vertices sharing an edge are **neighbours**
##### Neighbourhood
The **neighbourhood** $N$ of a vertex $v$ is the set of [[Introduction to ADS Graphs#Neighbours|neighbours]] $N(v)=\lbrace u\in V|uv\in E\rbrace$ 
##### Degree
The **degree** $deg(v)$ of a vertex $v$ is the number of [[Introduction to ADS Graphs#Neighbours|neighbours]] of $v$. $\delta(G)$ is the **smallest** degree whilst $\Delta(G)$ is the **largest** degree
##### Isolated Vertex
A vertex with [[Introduction to ADS Graphs#Degree|degree]] of **zero**
##### Pendant Vertex
A vertex with [[Introduction to ADS Graphs#Degree|degree]] of **zero**
##### Incident
An edge $uv$ is **incident** to $u$ and $v$
##### Adjacent
Where edges $uv$ and $vw$ are **adjacent** (share **one** vertex)
##### Subgraph
A **subgraph** $G^\prime=(V^\prime,E^\prime)$ of $G=(V,E)$ is a graph where $V^\prime\subseteq V$ and $E^\prime\subseteq E$ 
##### Proper Subgraph
A [[Introduction to ADS Graphs#Subgraph|subgraph]] $G^\prime$ where $G^\prime\neq G$ 
##### Spanning Subgraph
A [[Introduction to ADS Graphs#Subgraph|subgraph]] $G^\prime=(V^\prime,E^\prime)$ where $V^\prime\neq V$ 
##### Induced Subgraph
A [[Introduction to ADS Graphs#Subgraph|subgraph]] $G^\prime=(V^\prime,E^\prime)$ where $G^\prime$ contains **all** edges of $E$ where the two vertices are in $V^\prime$. This means we are simply removing the vertices and any edges connected to them, and nothing else
# Types of Graphs
## Directed Graphs

A **directed** graph is one where an edge is defined as an **ordered** pair of vertices, giving each edge the ability to "point" to one of its two vertices
## Multi-graphs

There may exist **multiple** edges between two vertices. This is useful when an edge represents a certain object linked to two vertices, and many objects share the same vertices
## Pseudo-graphs

Edges may connect to the **same** vertex (dubbed a **loop**)
## Weighted Graphs

Edges or vertices can be assigned **weights** such as numbers or qualities. Can be used for purposes such as representing distances
# Subsets of $V$

It is important to create subsets of vertices to satisfy certain qualities. It is often the purpose of algorithms to find one of these:
## Independent Set

A set of vertices where no two vertices are connected by an edge
## Maximum Independent Set

The largest [[Introduction to ADS Graphs#Independent Set|independent set]] for a given graph
## Minimum Colouring

The smallest set of [[Introduction to ADS Graphs#Independent Set|independent sets]] for a graph, where every vertex is in **exactly** **one** independent set
## Dominating Set

For a [[Introduction to ADS Graphs#Directed Graphs|directed graph]], a set of vertices that have an edge directed towards **every other** vertex in the graph
## Minimum Dominating Set

The largest [[Introduction to ADS Graphs#Dominating Set|dominating set]] for a given graph
# Handshaking

>[!quote] Theorem
>Let $G=(V,E)$ be a graph, $\sum\limits_{v\in V}deg(v)=2|E|$

This is mildly trivial, as each edge contributes **one** to the [[#Degree|degree]] of the **two** vertices it is connecting

>[!quote] Corollary
>In an **undirected** graph $G$, the number of vertices with an **odd** degree is **even**

This can proved using the handshaking theorem through **contradiction**. Assume the number of vertices with odd degrees were **odd**. Then the sum of all degrees will be odd, which **cannot** be equal to $2|E|$
# Special Graphs
## Complete Bipartite Graph

A **complete bipartite graph** $K_{p,q}$ is a graph consisting of two disjoint vertex sets on $p$ and $q$ vertices, and all possible edges between those sets (so it has $p\cdot q$ edges)

A **bipartite graph** is simply any [[#Subgraph|subgraph]] of $K_{p,q}$
## Complete Graph

A **complete** graph on $n$ vertices, denoted $K_n$, contains **all possible** edges between pairs of vertices 
## N-Cube

The **n-cube** $Q_n$ is a graph where:
$$V=\lbrace(e_1,\dots,e_n)|e_i\in\lbrace0,1\rbrace(i=1,\dots,n)\rbrace$$
In which two vertices are neighbours if, and only if, the corresponding rows differ in exactly one entry![[Pasted image 20250426212445.png]]
>[!quote] Theorem
>All n-cubes are [[#Complete Bipartite Graph|bipartite]]

Proof:

- Let $V_1$ and $V_2$ contain the vertices with an **odd** and **even** number of 1s
- This is a partition of $V$ into two disjoint sets, where each edge has an endpoint in each of the sets
- So it is **bipartite**