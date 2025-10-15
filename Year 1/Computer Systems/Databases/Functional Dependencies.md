Section: [[Year 1/Computer Systems/Databases/Databases (Root)]]
### Top-down Approach

- Start from data requirements
- Form a graphical description of the DB (an [[Entity Relationship Model]])
- Identify entities in the world, their attributes and relations
### Bottom-up Approach

- Start with actual data in tables
- Analyse relationships among attributes
- Normalise tables to redesign them in a *better* way
## Redundancy

Redundancy is the repeated storing of data. not only is this wasteful for storage space, but it may lead to inconsistencies (two different values for the same thing). This of course comes with the exception of **foreign keys**, as they are simply acting as **pointers**

Dependencies may cause redundancy. For example if, in the "student" table, there are fields "college" and "collegeAddress", then we have redundancy. This is because there are attributes not dependent on the primary key.

Redundancy can lead to the following anomalies:

- Insertion anomaly:
	- New records need to duplicate existing data
	- Cannot add partial records
- Modification anomaly:
	- Modifying values may lead to **inconsistency**
- Deletion anomaly:
	- Other data can be lost as a side effect of deleting one
## Decomposition

To avoid anomalies, we can decompose our tables to ensure that attributes are not dependent on non-key attributes. Consider this example, where "college" has been made the primary key of a new table, such that "collegeAddress" can be dependent on the primary key:
![[Pasted image 20250401140805.png]]
There are principles on how to decompose that rely on **functional dependencies** (such as $id\rightarrow college\rightarrow collegeAddress$)
## Functional Dependencies

These describe the relationships among attributes in the same relation. This can be used to determine which attributes to add to new tables when we **normalise**  

If $A$ and $B$ are two **sets** of attributes in a relation we can say that $B$ is **functionally dependent** on $A$ or $A\rightarrow B$. This means that each value of $A$ is associated with exactly one value of $B$. We also dub $A$ the **determinant** of $B$
### Full Functional Dependency

- $B$ is functionally dependent on $A$
- $B$ is not functionally dependent on any **proper subset** of $A$
- (any dependency on a single attribute is full)
### Partial Functional Dependency

- $B$ is functionally dependent on $A$
- $B$ is functionally dependent on at least one proper subset of $A$
### Transitive Functional Dependency

If $A\rightarrow B$ and $B\rightarrow C$ then $C$ is **transitively dependent** on $A$ via $B$
## Closure

 Given a set of functional dependencies $F$, its **closure** $F^+$ includes all functional dependencies implied by the dependencies in $F$

We need a set of inference rules to compute $F^+$, this brings us to **Armstrong's axioms**:

1. Reflexivity - If $B\subseteq A$ then $A\rightarrow B$
2. Augmentation - If $A\rightarrow B$ then $A,C\rightarrow B,C$
3. Transitivity - If $A\rightarrow B$ and $B\rightarrow C$ then $A\rightarrow C$

Along with the further derived:

4. Decomposition - If $A\rightarrow B,C$ then $A\rightarrow B$ and $A\rightarrow C$
5. Union - If $A\rightarrow B$ and $A\rightarrow C$ then $A\rightarrow B,C$
6. Composition - If $A\rightarrow B$ and $C\rightarrow D$ then $A,C\rightarrow B,D$

The closure $F^+$ of $F$ can be computed by repeatedly applying the above rules to the dependencies in $F$. Here is some pseudocode demonstrating this:

```
closure = F
repeat
	for each f in closure
		apply rules of reflexivity and augmentation to f
		add these new dependencies to closure
	for each pair f1, f2 in closure
		if f1 and f2 imply a new dependency using transitivity
			add the new function to closure
until closure does not change across an iteration
```
