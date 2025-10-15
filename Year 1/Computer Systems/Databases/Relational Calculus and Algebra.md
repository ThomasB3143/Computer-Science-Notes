Section: [[Year 1/Computer Systems/Databases/Databases (Root)]]

[[Relational Data Model#Terminology|Relations]] are considered sets of elements

An element is tuple of attribute values represented by one row of a table

Relational calculus and algebra are equivalent languages, as both can be used to define the same sets. A language such as [[SQL]] is **relationally complete** if it can produce any relation that relational algebra/calculus can
## Relational Calculus

Uses set theoretic expressions to define new sets based on existing ones, much like we have done in [[SQL]]

A **predicate** is a function that returns true or false when arguments are given

A **proposition** is the expression obtained when replacing values for the arguments of a predicate. Lets look at an example:

Example - Let $P(x)$ and $Q(x)$ be two predicates with argument $x$. We can define things such as the set of all $x$ such that $Q(x)$ is true and $P(x)$ is **not** true as:
$$\{x|Q(x)\land \sim P(x)\}$$
We focus on **tuple relational calculus**, where arguments are tuples. To specify that a tuple "s" should be in a relation "Staff", we use the predicate "Staff(s)". To retrieve the "name" from our tuple we use "s.name"

We can use the $\exists$ / "there exists" and $\forall$ / "for all" quantifiers for more complex predicates. Like this doozy of a set to get us the names of all staff working in a branch in London: 
$$\{s.name|\text{Staff}(s)\land(\exists b)(\text{Branch}(b)\land (b.\text{branchNo}=s.\text{branchNo})\land (b.\text{city}=\text{'London'}\}$$
## Relational Algebra

This uses operators to construct new sets from existing ones. It is a **procedural** language which specifies operations to construct a new set from existing ones:

| Unary                  | Binary                         |
| ---------------------- | ------------------------------ |
| Selection ( $\sigma$ ) | Union( $\cup$ )                |
| Projection ( $\pi$ )   | Set Difference ( $-$ )         |
| Rename ( $\varrho$ )   | Cartesian Product ( $\times$ ) |

From these **basic operations** we can **derive** new ones such as intersection, division and join
### Rename

- We often need to name intermediate expressions to reuse them
- We can use the rename operation to copy a relation with a new name
- $\uprho_{Y(A,B,C)}(X)$ will return $X$ renamed as $Y$ with attributes renamed as $A,B$ and $C$ 
- This is great when we need to reuse the same relation in different roles
### Selection

- $\sigma_{condition}(R)$
	- A unary operation with a [[Relational Data Model#Terminology|relation]] as an argument
	- It selects the subset of tuples from $R$ that satisfy the condition/predicate
	- Just like "SELECT * FROM R WHERE condition"
### Projection

- $\Pi_{col1,\;col2,\;\dots}(R)$   
	- Unary operation with a relation as an argument
	- Selects the specified subset of attributes from R
	- Eliminates duplicates unlike SQL (because its a set)
	- Just like "SELECT DISTINCT col1, col2 [, …] FROM R"
### Combining Selection and Projection

Suppose we want to retrieve the first and last name of each staff member earning over £40,000. We need to select the staff using [[Relational Calculus and Algebra#Selection|selection]] and [[Relational Calculus and Algebra#Projection|project]] our tuples onto our desired attributes like so:
$$\Pi_{\text{firstName, lastName}}(\sigma_{salary>40000}(\text{Staff}))$$
### Union

- $A\cup B$ 
	- Binary operation on two relations
	- Selects tuples that are in A or B and adds them together into a new relation
	- REMOVES DUPLICATES (its a set)
	- Corresponds to "SELECT . . . UNION SELECT . . ."
### Set Difference

- $A - B$
	- Binary operation on two relations
	- Selects tuples that are in A but **not** in B
	- Removes all tuples from a copy of A that are also in B
	- Corresponds to "SELECT . . . MINUS SELECT . . ." or "SELECT . . . EXCEPT SELECT . . . "
### Intersection

- $A\cap B$
	- Binary operation on two relations
	- Selects tuples that are in A and in B
	- Corresponds to "SELECT . . . INTERSECT SELECT . . ."
	- Derived from $A\cap B=A-(A-B)$
### Union Compatibility

To compute any of the above three:

- The **schemata** of A and B must match:
	- Same number of attributes
	- Each pair of attributes needs the same **domain**
	- Attributes names are ignored
- We say they are **union compatible**

We can use [[Relational Calculus and Algebra#Projection|projection]] to get to this state
### Cartesian Product

- $A\times B$
	- Binary operation on two relations
	- Returns all possible combination of tuples in A and B through **concatenation**
	- There will be $r_Ar_B$ tuples with $a_A+a_B$ attributes
	- No compatibility requirements like with [[Relational Calculus and Algebra#Union Compatibility|unions]]
	- Corresponds to "SELECT * FROM A, B" or "SELECT * FROM A CROSS JOIN B"
### Division

- $A\div B$ 
	- Binary operation on two relations
	- Only keeps tuples from A that exist in all possible combinations with B
	- Not part of SQL but appears often in practice
	- We could use this to select all of the clients that have viewed **every** property or something like that
	- B has a **subset** of attributes from A
	- We find all possible combinations and only keep tuples and attributes that are in A
	- Project both relations to attributes only in A, then remove the previous combinations from A
	- $A\div B=\Pi_{X1,X2,\dots}(A)-\Pi_{X1,X2,\dots}((\Pi_{X1,X2,\dots}(A)\times B)-A)$   
### Cheat Sheet

![[Pasted image 20250405154105.png]]
