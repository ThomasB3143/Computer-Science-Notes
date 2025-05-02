Section: [[Propositional Logic (Root)]]
## Pure Literals

YOU DO NOT NEED THIS FOR YOUR SAT SOLVER

A literal is a pure literal of a clause set if no clause contains its **negation** (check [[SAT Solving|here]] if you've forgotten what a clause is)

We can remove all clauses that contain pure literals to form a new **equisatisfiable** clause set.

This is **pure literal elimination**

Example - Apply PL **repeatedly** to $\{\{x,y\},\{\lnot y,\lnot z\},\{z,x\}\{u,\lnot z\}\}$

First we remove all clauses with $x$ and $u$ to get $\{\{\lnot y,\lnot z\}\}$ 

Now $\lnot y$ and $\lnot z$ are our pure literals, so we can remove them to get the empty clause set

This is equisatisfiable to our original clause set
## Unit Propagation

When a clause set contains a unit clause (a clause with one literal)¦, we can remove all occurrences of that literal from all clauses to form a new **equisatisfiable** clause set

Example - Apply UP **repeatedly** to $\{\{x,y\},\{\lnot y\},\{z,\lnot x,v\}\}$

First we remove all instances of $y$ to get $\{\{x\},\{z,\lnot x,v\}\}$ 

Then we remove all instances of $x$ to get $\{\{z,v\}\}$ 

This is equisatisfiable to our original clause set