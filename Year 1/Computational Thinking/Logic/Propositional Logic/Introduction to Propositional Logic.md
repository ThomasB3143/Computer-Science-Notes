Section: [[Propositional Logic (Root)]]

This is the most fundamental [[Introduction to Logic|logic]], utilising **propositions** (declarative sentences that resolve to "true" or "false").

## Syntax

Propositions are represented by propositional variables (Booleans), and new propositions (formulae) can be formed from these variables through **logical operators**

- $\land$  (and)
- $\lor$ (or)
- $\lnot$ (not)
- $\implies$ (implies)
- $\iff$ (if and only if)

This is the **syntax** for the logic, each operator takes two propositional formulae and yields a new one (except for $\lnot$ ). Parenthesis can be used like so:

$(A\land B)\lor C$ means build $A\land B$ and then build $(A\land B)\lor C$

## Semantics

All propositional variables take the value "true" or "false", and the value of a formula under some **truth assignment** (this is when we assign "true" or "false" to each variable) can be obtained using a **truth table** like so:

| $p$ | $q$ | $p\land q$ | $p\lor q$ | $\lnot p$ | $p\implies q$ | $p\iff q$ |
| :-: | :-: | :--------: | :-------: | :-------: | :-----------: | :-------: |
|  T  |  T  |     T      |     T     |     F     |       T       |     T     |
|  T  |  F  |     F      |     T     |     F     |       F       |     F     |
|  F  |  T  |     F      |     T     |     T     |       T       |     F     |
|  F  |  F  |     F      |     F     |     T     |       T       |     T     |
We say that a formula **evaluates** to a Boolean under a given truth assignment. If it evaluates to true when we say the assignment **satisfies** the formula.

If the formula evaluates to true regardless of assignment (like $A\lor\lnot A$ ) then it is a **tautology**, if it always evaluates to false (like $A\land\lnot A$ ) then it is a **contradiction**. A **literal** is the negation of a propositional variable or just a plain old propositional variable (like $X$ or $\lnot X$ )

## Logical Equivalence

Steps in proof are often replacing a statement with another such as this:

$X\implies Y = \lnot X\lor Y$ 

Two formulae are **logically equivalent** if they have identical truth tables (using the $\equiv$ symbol)

## De Morgan's Laws

Really useful logical equivalencies, best used for simplifying a formula:

$\lnot(A\land B)\equiv\lnot A\lor\lnot B$
$\lnot(A\lor B)\equiv\lnot A\land\lnot B$

This also implies that:

$\lnot(A\land B\land C)\equiv\lnot A\lor\lnot B\lor\lnot C$
$\lnot(A\lor B\lor C)\equiv\lnot A\land\lnot B\land\lnot C$

## Distribution Laws

Also good one's to have in the bank, similar to the expansion of brackets:

$A\lor(B\land C\land D\dots)\equiv(A\lor B)\land(A\lor C)\land(A\lor D)\dots$

$A\land(B\lor C\lor D\dots)\equiv(A\land B)\lor(A\land C)\lor(A\land D)\dots$

## Functional Completeness

We used a specific set of [[Introduction to Propositional Logic#Syntax|connectives]] earlier, but you could use another set (like NAND and NOR). A set is only **functionally complete** when it can be used to represent any propositional formula (or equivalently any truth table)

## Disjunction and Conjunctions

A **conjunction** is a sequence of **literals** and $\land$ operators, whereas a **disjunction** is a sequence of **literals** and $\lor$ operators.

We can prove that any formula $\psi$ can be represented as a disjunction of conjunctions (**disjunctive normal form/DNF**) like so:

- Say $\psi$ involves variables $p_1,p_2,\dots,p_n$ and therefore has $2^n$ truth assignments
- Let $f$ be a truth assignment evaluating to **true**
- For all variables, if $p_i$ is true then include $p_i$ in the conjunction, otherwise include $\lnot p_i$ in the conjunction
- Do this for all $f$ in $\psi$ and create a disjunction of each of the conjunctions, voila

Using this idea we can also express the same formula as a conjunction of disjunctions (**conjunctive normal form/CNF**) like so:

- Convert $\lnot\psi$ into DNF instead of $\psi$
- $\psi$ is equivalent to $\lnot\lnot\psi$ thus using [[Introduction to Propositional Logic#De Morgan's Laws|De Morgan's law]] we can equate this to a conjunction of conjunctions, each with a $\lnot$ operator around them
- Then we use the law again on each inner conjunction to form a final conjunction of disjunctions

The concept of CNF is required for [[SAT Solving]]
