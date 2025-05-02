Section: [[Databases (Root)]]

A **Data Definition Language** (DDL) is too low-level, hence we need a more abstract and mathematically sound data model to describe structure. This brings us to the…
## Relational Data Model

- Based on mathematical relations
- Relations are stored in tables
	- A schema of a relation R: $R(A_1,A_2,\dots,A_n)$ has attributes $A_1,A_2,\dots,A_n$
	- For example: $Student(studentNo, prename, surname)$
	- Ordering of attributes does not matter
### Terminology

- Relation: Table
- Attribute: Uniquely named column in a table
- Tuple: A row in a table representing 
- Domain: a set of allowed values for an attribute
- Cell: The value of a specific attribute in a tuple
- Degree: Number of attributes in a relation
- Cardinality: Number of tuples in a relation
- Relational Database: A collection of normalised relations
![[Pasted image 20250331132625.png]]
NULL indicates the absence of a value, this could be one that is **currently unknown** or **not applicable**. It is not a normal value and must be handled in a special way
## Keys

- Uniquely identify a tuple in a relation
- A set of attributes whose values can uniquely determine a tuple
- Candidate key: The minimal set of attributes that is a key
- Primary key: One candidate key selected to identify couples
- Alternate key: Any candidate key that is *not* the primary key
- Simple key: A key with a single attribute
- Composite key: A key with multiple attributes
### Foreign Keys

A key in a relation referencing the primary key of another relation in a relational database.
### Integrity Constraints

- Domain constraints (we talked about this)
- Entity Integrity:
	- Attributes of a primary key cannot be NULL
	- Ensures each entity has a unique identifier
	- And that foreign key values form proper references
- Referential Integrity
	- Foreign keys must match a primary key or be NULL
	- Prevents deleting tuples that are referenced elsewhere
## Views 

So far we have only looked at base relations. A **view** is a different type of relation, derived from **base relations**. They are computed upon request by the user.

These are used to show customised information to the user through **information hiding** as well as compute dynamic quantities (like age from a DOB)
## Network Data Model

- Record Based
- Tuples are nodes in a graph
- Relationships are edges
## Hierarchical Data Model

- Each node has a parent and many children
- Like a tree!