Section: [[Propositional Logic (Root)]]

The aim of this method is to encode a problem as a [[Introduction to Propositional Logic|propositional]] formula such that every satisfying truth assignment corresponds to a solution to the problem, and then finding such a truth assignment for the formula, and in doing so solving the problem. This requires an input to be in [[Introduction to Propositional Logic#Disjunction and Conjunctions|CNF]].

A **clause** is a non-[[Introduction to Propositional Logic#Semantics|tautological]] disjunction of literals, and thus CNF is a conjunction of clauses.

If each clause contains $k$ literals, we have the k-SAT problem. If we have a formula where each variable appears in a maximum of $s$ then we have the (k,s)-SAT problem.

But these are all NP-complete for $k\geq 3$ 

