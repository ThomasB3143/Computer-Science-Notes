Section: [[Databases (Root)]]

Normalisation is a multi-step process that converts a database into a **normal form** at each step. To do this it must fulfil certain requirements including achieving the form in the previous step
## 1st Normal Form

There must be no repeating groups (every cell has one value). If there is a fixed number of repetitions we can simply decompose the attribute into separate attributes. Otherwise, we need to **flatten** by filling empty cells with repeated values or create a new **relation**
## 2nd Normal Form

Every non-key attribute must be dependent on the **whole** primary key ([[Functional Dependencies#Full Functional Dependency|full functional dependency]]). Note that this is only relevant for relations with **composite keys**
![[Pasted image 20250401203307.png]]
Here we see that "rent", "pAddress", "rentStart" and "rentFinish" are **partially** dependent on the primary key. We need to construct some new tables to solve this:![[Pasted image 20250401203457.png]]
We have removed the partially dependent attributes and placed them in a new relation alongside their determinant
## 3rd Normal Form

Every relation must contain no [[Functional Dependencies#Transitive Functional Dependency|transitive functional dependencies]]. See the following example:![[Pasted image 20250401203710.png]]
"propertyNo" determines "ownerNo" which determines "oName", which violates our requirement. To solve this, we remove transitively dependent attributes and place them in a new relation alongside a copy of their determinant, like this:![[Pasted image 20250401203938.png]]
