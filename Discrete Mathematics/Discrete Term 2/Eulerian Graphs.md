Section: [[Discrete Term 2 (Root)]]
## Travelling

A **walk** is a sequence, alternating between vertices and edges, like $v_1e_1v_2e_2\dots e_{k-1}v_k$ where the edges and vertices need not be distinct

The **length** of a walk is the number of edges in a walk

A walk is **closed** if the first and final vertices in the walk are identical

A **trail** is a walk with no edge repeated (but vertices can be)

A **circuit** is a closed trail

A **path** is a walk with no vertices or edges repeated

A **cycle** is a closed path

Paths are cycles are stricter types of trails and circuits that do not allow repeated vertices\

Theorem - If a graph has a walk between two vertices, it has a path between them also

This is true as if a walk does not repeat any vertex then it is a path. If it does repeat a vertex then all parts of the sequence between the two appearances of the vertex can be removed as well as one copy of the vertex. Repeat this until all vertices are unique and you have a path!
## Connectedness

A graph is **connected** when every pair of vertices has a path between them

For a given graph, a **connected component** makes up the maximal set of connected [[Introduction to Graphs#Subgraphs|subgraphs]]

Vertices in the same component have a path between them

A bridge is an edge such that its removal will increase the number of connected components
## Bridges of Konigsberg

Basically trying to visit every vertex in a single [[Eulerian Graphs#Travelling|circuit]]

A graph upon which such a circuit can be constructed is **eulerian**
## Euler's theorem

Theorem - A graph is eulerian if and only if all vertices have an even degree

Lemma 9.5 - If a graph is finite and connected, with even degree vertices, then it is a finite union of edge-disjoint cycles

We can prove this because any graph where all vertices have a degree greater than 1 contains a cycle. We can repeatedly remove cycles which decreases the degree of the included vertices by 2, maintaining an even degree. If we repeat this until the graph is null, then we have decomposed the graph into edge-disjoint cycles

Now we can prove the theorem that these $n$ edge-disjoint cycles can be combined into a single Euler circuit:

Base case - if $n=1$ then one cycle is the euler circuit

Inductive step - we are going to assume that if $G$ is made up of $\leq n-1$ edge-disjoint cycles labelled $C_1,C_2\dots C_n$, it has an euler circuit. Now we consider a graph of $n$ cycles

We can remove the cycle $C_n$ to form a new graph $H$. This graph may not be connected so we consider its components $H_1,H_2\dots H_k$

Each cycle must be within a component, and each component contains at least once cycle. Hence $k\leq n-1$

Using our assumption earlier, we can assume that all components of $H$ are eulerian since they are made up of $\leq n-1$ edge-disjoint cycles

But $G$ was connected, hence $C_n$ must visit each component of $H$. So we can form an euler circuit by following $C_n$, but for each eulerian circuit we encounter, we follow it around before continuing