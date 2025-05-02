Section: [[Graph Theory and Algorithms (Root)]]
# Terminology

This chapter is a **lot** of terminology, get ready...
## Walk

A **walk** in a graph $G$ is a sequence of **edges** $v_0v_1,v_1v_2,\dots v_{n-1}v_n$ or a sequence of **vertices** $v_0,v_1,\dots,v_n$
## Circuit

A **circuit** is a closed [[#Walk|walk]], where $v_0=v_n$
## Path

A **path** is a [[#Walk|walk]] if all vertices are **distinct
## Cycle

A **cycle** is a closed [[#Path|path]], where $v_0=v_n$
## Length

The **length** of any of the above sequences is the number of **edges**
## Distance

The **distance** $dist(u,v)$ between vertices $u$ and $v$ in a graph is the [[#Length|length]] of the **shortest** path between them (or $\infty$ if one does not exist)
## Diameter

The **diameter** is the greatest [[#Distance|distance]] in a graph
# Shortest-Path Problems

In a graph, potentially with **edge weights**, there exists the common problem of computing a path between to vertices with the **shortest** possible [[#Distance|distance]]. Remember this for later
# Connectivity

>[!quote] Definition
>A graph is connected if there exists a path between **every** pair of vertices in $G$

A **connected component** of a graph is a **maximal** connected subgraph (meaning it cannot be given any more vertices whilst remaining connected)

>[!quote] Theorem
>Every graph $G=(V,E)$ contains at least $|V|-|E|$ connected components

Proof:

- By induction over $m=|E|$
- Induction basis: m = 0 means no edges, hence we have $|V|=|V|-|E|$ connected components
- Induction step: Consider a graph $G$ with $|E|=m+1$ and arbitrary $e\in E$ and define $E^\prime=E\setminus \lbrace e\rbrace$. Now $G^\prime(V,E^\prime)$ has at least $|V|-m$ components. Here we are given **two** cases:
	1. With $e$, the number of connected does not change
	2. With $e$, the number of connected components decreases by $1$
- In both cases, the $G$ has at least $|V|-|E|$ connected components
## Strong Connectivity

A [[Introduction to ADS Graphs#Directed Graphs|directed graph]] $G$ is **connected** if the graph obtained from $G$ by forgoing directions is still connected. However, it is only **strongly connected** if any two vertices are connected by **directed paths** in both directions
# Eulerian Circuits

A [[#Circuit|circuit]] that visits **every edge** in a graph exactly once

>[!quote] Theorem
>A connected graph with at least two vertices has an Eulerian circuit if, and only if, each of its vertices has even [[Introduction to ADS Graphs#Degree|degree]]

Proof:

Each time a circuit passes through a vertex $v$ it contributes $2$ to the degree of $v$. Since each edge is used once, the degree of $v$ must be **even**. This gives us our **Necessity** $(\implies)$

We know perform **proof by induction** to get **Sufficiency** $(\impliedby)$ 

- Induction basis: $G=K_3$ (recall [[Introduction to ADS Graphs#Complete Graph|complete graphs]])
- Induction step:
	- Begin walking from any vertex $u$ along untraversed edges, marking off traversed edges
	- Stop when arriving at a vertex with no edges unmarked, this vertex must be $u$ again
	- Hence we have a circuit $C$, delete it from $G$ to obtain a smaller graph $H$ with all even degrees
	- Each connected component of $H$ has an eulerian circuit
	- Combine $C$ and these circuits to obtain the eulerian circuit for $G$
# Hamiltonian Cycles

A [[#Cycle|cycle]] which visits each vertex **exactly once**

This is an **NP-complete** problem
# Travelling Salesman Problem 

The **Travelling Salesman Problem** (TSP) seeks to find the [[#Cycle|cycle]] on a [[Introduction to ADS Graphs#Weighted Graphs|weighted graph]] of the **lowest total weight**

We can actually map this problem to that of finding a [[#Hamiltonian Cycles|Hamiltonian cycle]] by setting the cost of traversing between **neighbours** $1$ and $2$ for non-neighbours. This is a **reduction** of one problem to another!!!