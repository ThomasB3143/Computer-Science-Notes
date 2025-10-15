Section: [[Discrete Term 2 (Root)]]

>[!quote] Definition
>A **planar graph** is one that can be drawn in a 2D plane, such that no edges meet except at their endpoints
# Faces and Boundaries

A planar representation of a graph divides the plane into **faces**, an area enclosed by edges. The **boundary** of a face is the closed walk around it

Every edge has two sides, but may bound the same face

The planar representation of any graph has an infinite face

Two planar representations with different boundary lengths of faces are **essentially different**
## Planar Handshaking

Where $b(f)$ is the boundary length of $f$:
$$\sum^{}_{f\in F}b(f)=2|E|$$
# Euler's Formula

Let $G=(V,E)$ be a planar graph with set of faces $F$ and $k$ connected components:
$$|V|-|E|+|F|=k+1$$
# Very Few Edges

>[!quote] Theorem 10.5
>If $G=(V,E)$ is a simple planar graph with $|V|\geq3$, then $|E|\leq3|V|-6$
# Girth

>[!quote] Definition
>The **girth** $g$ of $G$ is the shortest length of a cycle of $G$. $g=0$ when $G$ has no cycles

We know that:
$$|E|\leq\frac{g}{g-2}(|V|-2)$$
# Subdivisions

>[!quote] Definition
> A **subdivision** of $G$ is some $G$ where edges are divided into two edges joined by a new vertex

This means that if $G$ is planar, its subdivision is also planar. But here is a massive proof that we have no idea how to prove ourselves:

>[!quote] Theorem
>$G$ is not planar $\iff$ $G$ contains a subdivision of $K_5$ or $K_{3,3}$

Like that one? Here's another:

>[!quote] Theorem
>Every simple planar graph has **at least one** vertex of degree $\leq5$

This is clearly true for $V\leq6$. But for all graphs where $|V|>6$ we can start by assuming that all degrees are $\geq6$.

This means that $2|E|=\sum d(v)\geq6|V|$ hence $|E|\geq3|V|$

But wait, remember that planar graphs have [[#Very Few Edges]], so $|E|\leq3|V|-6$. This contradiction proves our original theorem
# Platonic Graphs

>[!quote] Definition
>A **Platonic** graph is finite, simple, planar and connected, with vertices of the same degree $d$ and faces of the same boundary length $b$

There are only 5 of these, here is the proof:
$$d|V|=2|E|=b|F|$$
$$|V|-|E|+|F|=k+1\implies |V|-\frac{d|V|}{2}+\frac{d|V|}{b}=2$$
$$|V|(2b-bd+2d)=4b,|V|>0 ,b>0\implies(b-2)(d-2)<4$$
This equation has 5 integer solutions, where $b,d>0$:

| $d$ | $b$ | $\|F\|$ | Shape        |
| --- | --- | ------- | ------------ |
| 3   | 3   | 4       | tetrahedron  |
| 3   | 4   | 6       | cube         |
| 4   | 3   | 8       | octahedron   |
| 3   | 5   | 12      | dodecahedron |
| 5   | 3   | 20      | icosahedron  |
Look familar?

![[Pasted image 20250530212821.png]]