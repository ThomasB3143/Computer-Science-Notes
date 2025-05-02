---
~
---
Section: [[Databases (Root)]]
## Three-Level ANSI-SPARC Architecture

An architecture comprised of:

- External Level
	- The user's view of the DB
	- Different views of the same data for specific needs
	- Possibly derived (like how age is combined from DOB)
- Conceptual Level
	- Community view of the DB
	- Shared by all users
	- Describes what data is stored in the DB (entities, attributes etc)
	- Essentially the **logical structure** needed to support views on the external level
	- NO storage-specific details (purely theoretical)
- Internal Level
	- Physical representation of the DB
	- The **how**
	- Designed to achieve optimal runtime performance and space utilisation

We typically focus on the **conceptual level**
## Database Schema/Instance 


A database schema is the complete description of a database, constant regardless of the entities added.

A database instance is concrete data in the database at a point in time. This changes whenever data is inserted, updated or deleted and it is apparent that many instances may correspond to the same scheme (they are basically states of a DB)
## Data Independence

![[Pasted image 20250331120019.png]]
- Logical Data Independence:
	- Views of the database remain the same if we change the logical structure
- Physical Data Independence:
	- Conceptual schema remains the same if we change the internal schema
## Database Design
### Conceptual Design

- Construct a high-level Model using entity-relationship modelling. Identify necessary entities, attributes and relationships
- Base on the user requirements
- Independent of physical considerations
- Provides a fundamental understanding of the system
### Logical Design

- Construct the relational data model
- Use normalisation techniques to eliminate data redundancy and anomalies
### Physical Design

- Implementation of the logical design
- Considering:
	- Storage structures
	- Access methods
	- Security protection
- Optimised for performance
