Section: [[Graph Theory and Algorithms (Root)]]

>[!quote] Defintions
>A **forest** is a graph containing no [[Paths, Cycles and Trees#Cycle|cycles]]
>A **Tree** is a [[Paths, Cycles and Trees#Connectivity|connected]] forest

# Spanning Trees

Recall [[Introduction to ADS Graphs#Spanning Subgraph|spanning subgraphs]], allow us to prove the following:

>[!quote] Theorem
>Every connected graph contains a **spanning tree**

Proof:

Let $G$ be a connected graph
- If $G$ contains no cycles, then it is a tree, and a spanning tree of itself
- If $G$ contains a cycle, we can remove one edge from the cycle and leave a connected subgraph (you can still go around the cycle segment to get between the now non-neighbouring vertices)
- Repeat this until there are no more cycles

It is often the case that we want the **minimum-weight spanning tree**
# Leaves

> [!quote] Definition
> A **leaf** in a tree is a **vertex** with [[Introduction to ADS Graphs#Degree|degree]] of $1$

>[!quote] Lemma
>Every tree on at least two vertices contains a leaf

We can prove this by contradiction. If there were no leaves, we could begin a walk where we can always leave a vertex we traverse to. Eventually we will have to return to our start vertex, meaning we have a **cycle** (and it is NOT a tree)
# Edges in Trees

>[!quote] Theorem
>A connected graph on $n$ vertices is a **tree** if, and only if, it has $n-1$ edges

Proof:

We can prove **neccesity** by induction! The theorem holds for $n=1$ and $n=2$, thus establishing our **induction basis**. Now for our **induction step**:

- Suppose each tree on $n-1$ vertices has $n-2$ edges
- Take a tree $T$ on $n$ vertices
- $T$ contains a [[#Leaves|leaf]]. Consider the graph $T-v$, it has one vertex and edge less than $T$
- $T-v$ is still a tree with $n-1$ vertices, by induction hypothesis it has $n-2$ edges
- $T$ has one more edge, hence $n-1$ edges

Now for our **sufficiency**:

- Assume that $G$ is a connected graph with $n$ vertices and $n-1$ edges
- $G$ contains a spanning tree $T$ (as per the previously established [[#Spanning Trees|proof]])
- $T$ contains exactly $n-1$ edges (we just proved this)
- $T$ is a **subgraph** of $G$ and has the same number of **edges** as $G$
- Hence $T$ and $G$ are the **same**
- So $G$ is a **tree**
# Paths in Trees

>[!quote] Lemma
>There exists a **unique path** between any vertices $u$ and $v$ in $T$

Lets prove this by **contradiction**:

Were there two paths $P$ and $Q$ between $u$ and $v$. There exists vertices $x$ and $y$ on both $P$ and $Q$, such that between $x$ and $y$ the vertices between the paths are **disjoint**

The segments of $P$ and $Q$ between $x$ and $y$ form a **cycle**, therefore $T$ cannot be a tree and we have a **contradiction**
# Rooted Trees

>[!quote] Definition
>A **rooted tree** is a tree in which one vertex is designated the **root**

We often draw a rooted tree in **levels**, where each level $n$ holds the vertices at [[Paths, Cycles and Trees#Distance|distance]] of $n$ from the root![[Pasted image 20250426232711.png]]
## Children

Let $v$ be a vertex in a rooted tree. The **neighbours** of $v$ in the next **level** are referred to as the **children** of $v$
## Parent

The **unique** neighbour of $v$ in the previous **level** is called the **parent** of $v$
## Leaf

A vertex with no [[#Children|children]] is a **leaf**
## Internal

An **internal** vertex is one **with** [[#Children|children]]
# Isomorphism

>[!quote] Definition
>Two graphs $G$ and $G^\prime$ are **isomorphic** if there exists some bijective function $f:V\rightarrow V^\prime$, such that for every $u,v\in V$ we have $uv\in E\iff f(u)f(v)\in E^\prime$
>We say that $G\cong G^\prime$

This basically means that the graphs have the same **layout**, or there is some "renaming" of vertices between $G$ and $G^\prime$
## Rooted Isomorphism

Two [[#Rooted Trees|rooted trees]] are only isomorphic if the root of the first tree maps to the root of the second tree. As shown in the example below, $T_1$ and $T_2$ are isomorphic as **graphs** but not as **rooted trees**:
![[Pasted image 20250427151015.png]]

We actually have an algorithm for determining if two rooted trees are **isomorphic**:
##### LabelVertex($T$,$v$)
```
if v is leaf then
	label(v) = 10
else
	for every child w of v do
		l(w) = LabelVertex(T,w)
	Sort all l(w) in decreasing order so l(w1) >= l(w2) >= ... >= l(wk)
	label(v) = "1" + l(w1)l(w2)...l(wk) + "0"
return label(v)
```

This algorithm can be used like so, to determine the isomorphism of two rooted trees:

```
if LabelVertex(T1,r1) == LabelVertex(T2,r2) then
	T1 and T2 are isomorphic
else
	T1 and T2 are NOT isomorphic
```

![[Pasted image 20250427152233.png]]
