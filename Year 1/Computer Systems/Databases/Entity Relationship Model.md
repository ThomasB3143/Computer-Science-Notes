Section: [[Year 1/Computer Systems/Databases/Databases (Root)]]

An ER Model is a conceptional database design free of technicality and ambiguity. It consists of:

- - Not identical to the [[Relational Data Model]]
- Top-down approach to database design
- Entities:
	- A "thing" that must be explicitly represented, such as a student or a course.
	- Holds **attributes**:
		- Can be **simple** (only one component)
		- Or **composite** (multiple components)
		- Can be **single valued** (one value per occurrence)
		- Or **multi-valued** (multiple values per occurrence)
		- Can apply constraints to numbers in the form "min..max"
		- Derived values, prefixed with a /, can be computed from other attributes
	- An entity **type** is a class of all objects with similar properties
	- An entity **occurrence** is a single instance of an entity type
- Relationships:
	- A named association between two or more entity types
	- Such as a student "attending" a course, or a recipe "requiring" an ingredient
- Constraints:
	- On the multiplicity of a relation
	- Commonly a range in the form "min..max"
	- For example, the constraint on "student takes courses" could be 1..* as a student must be taking at least one course (and generally can take as many courses as they wish)
## Why choose this over [[Relational Data Model]]?

The relational data model is much more low-level and technical. The abstractions brough by an ER model makes it easy to understand and formulate data requirements, and highly intuitive to work with.
![[Pasted image 20250401133425.png]]
## Transforming to a [[Relational Data Model]]

An ER model is a **logical** design, and we need to form our tables and attributes to handle the relations we have defined:
### One-to-One Relationships

- Add a foreign key to the **mandatory** identity
- If both are mandatory, consider merging them into one relation
- If both are optional, either direction is fine
### One-to-Many Relationships

- Add the foreign key of the "one" to the "many"
- For example, if a course has one teacher and a teacher may teach many courses, the **course** will contain a foreign key for a teacher
### Many-to-Many Relationships

- Create a separate relation (a link table) with the two foreign keys
- Each relation will have a one-to-many relation with the link table
## Constructing an ER Model

1. Identify entities and relationships
2. Draw entities and connect
3. Add constraints
4. Resolve [[Entity Relationship Model#Many-to-Many Relationships|Many-to-Many Relationships]]
5. Add attributes and define primary keys
6. Repeat and refine