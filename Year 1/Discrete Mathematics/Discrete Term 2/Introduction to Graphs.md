Section: [[Discrete Term 2 (Root)]]
## Basic definitions

Graphs are **Vertices** joined by **edges**

More formally, a **simple** graph $G$ is a pair of sets $V$ and $E$, where each element of $E$ is a 2-element subset of $V$

**Endpoints** are the two vertices connected to the edge

Two vertices are **adjacent** if there exists an edge between them

A vertex is **isolated** when it is adjacent to no other vertex

An edge is **incident** to a vertex if that vertex is an endpoint of the edge

The **degree** of a vertex is the number of times the vertex appears as an endpoint of an edge, in a simple graph this is the number of adjacent vertices

A **leaf** is a vertex of degree 1
## Standard Simple Graphs

**Empty/Null graph** - Denoted as $N_m$, a graph where $|V|=m$ but $|E|=0$

**Complete graph** - Denoted as $K_m$, a graph where each $|V|=m$ and $\forall v\in V,d(v)=|V|-1$

**Star graph** - Denoted as $S_m$, one of the $m$ vertices is connected to all other vertices, which each are [[Introduction to Graphs#Basic definitions|leaves]]

**Wheel graph** - Denoted as $W_m$, a star graph where the leaves have been connected to each other in the order that they can be listed in

**n-cube** - denoted as $Q_n$, a graph with $2^n$ vertices where, if each vertex were labelled by an n-digit binary string, the edges exist between vertices whose strings differ by one digit.
## Handshaking

For any graph, the sum of degrees is double the number of edges
This means that the number of odd-degree vertices must be even. More formally:

$\sum\limits^{|V|}_{n=1}d(v_n)=2|E|$
## Graph Isomorphism

Two graphs $G_1,G_2$ are **isomorphic** if there exists a bijective function $\varphi:V_1\rightarrow V_2$ that preserves adjacency such that $xy\in E_1$ and $\varphi(x)\varphi(y)\in E_2$

We write this as $G_1\cong G_2$
## Complements

The **complement** of graph $G=(V,E)$ is $\overline{G}=(V,F)$, where $F$ consists of all possible edges except for the ones that exists in $E$

Basically $\overline{G}$ has all the other edges
## Subgraphs

If $G=(V,E),G_1=(V_1,E_1),V_1\subseteq V,E_1\subseteq E$ then $G_1$ is a subgraph of $G$

We use $G_1\subseteq G$ to show this