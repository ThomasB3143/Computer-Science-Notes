Section: [[Digital Electronics (Root)]]

Highlighting anything that isn't just the basics here, you already know most of this without notes (like what an AND is)
# Functionally Complete Sets

A **functionally complete** set of Boolean operators is one which can express all possible truth tables by combining members of the set into a Boolean expression. Here are the common examples:

- AND, OR and NOT
- NAND
	- (a NAND b) NAND (a NAND b) = a AND b
	- (a NAND a) NAND (b NAND b) = a OR b
	- a NAND a = NOT a
- NOR
	- (a NOR b) NOR (a NOR b) = a OR b
	- (a NOR a) NOR (b NOR b) = a AND b
	- a NOR a = NOT a

NAND gates are easier to make (less silicon for same performance), so often used as universal gates 
# Circuits

A network that processes discrete-valued variables, it has:

- One or more discrete valued inputs
- One or more discrete valued outputs
- A specification of the relationship between inputs and outputs
- A specification of the delay between inputs and outputs changing
- Elements - In itself a circuit (this defines a circuit recursively)
- Nodes - A wire joining elements. Its voltage contains a discrete valued variable
# Combinatorial Logic 

- Individual gates are combinatorial circuits
- Every circuit element must be a combinatorial circuit
- Every node is an input to the circuit or connecting to **exactly one** output of a circuit element
- The circuit has no cyclic paths
# Boolean Algebra

Any variable $A$ or its compliment $\bar A$ is called a **literal**

The AND of several literals is called a **product**, denoted $A\cdot B\cdot C$


A **minterm** is a product in which all inputs to a function appear once each (either complimented or uncomplimented)

The OR of several literals is called a **sum**, denoted $A+B+C$

A **maxterm** is a sum in which all inputs to a function appear once each (either complimented or uncomplimented)
## Sum of Products

We can OR together the rows outputting 1 in a truth table, whilst ANDing the variables in the row. Take the example truth table

| A   | B   | Output |
| --- | --- | ------ |
| 0   | 0   | 0      |
| 1   | 0   | 1      |
| 0   | 1   | 0      |
| 1   | 1   | 1      |
This leaves us with $(A\cdot\overline B)+(A\cdot B)$ as our **sum of products**

## Product of Sums

We can AND together the rows outputting 0 in a truth table, whilst ORing the **negation** of variables in the row. Take the example truth table

| A   | B   | Output |
| --- | --- | ------ |
| 0   | 0   | 0      |
| 1   | 0   | 1      |
| 0   | 1   | 0      |
| 1   | 1   | 1      |
This leaves us with $(A+B)\cdot(A+ \overline B)$ as our **product of sums**