Section: [[Propositional Logic (Root)]]

Recall the rule of [[Proof Systems#Resolution|resolution]] for [[Introduction to Propositional Logic|propositional logic]], the process of resolution is used to take a given formula and decide whether it is a [[Proof Systems#Theorems|theorem]] or not

- Given a propositional formula $F$
- Take $\lnot F$ and represent it in [[Introduction to Propositional Logic#Disjunction and Conjunctions|CNF]] as $C_1\land C_2\land\dots\land C_m$
- Begin with clauses $C_1,C_2,\dots, C_m$
- Continually apply resolution to infer new clauses:
	- If we infer an empty clause then we halt and output that $F$ is a theorem
	- If we cannot infer any new clauses then we output that $F$ is **not** a theorem

This is both [[Proof Systems#Soundness|sound]] and [[Proof Systems#Completeness|complete]] as if resolution announces that $F$ is a theorem then $F$ is a tautology, and if $F$ is a tautology then resolution announces that $F$ is a theorem

Example - consider this set of clauses

$\begin{matrix}1.&2.&3.&4.&5.&6.&7.\\\lnot A\lor \lnot B\lor C&A\lor D&B\lor E&\lnot C&\lnot F\lor\lnot D&\lnot F\lor\lnot E&F\end{matrix}$

Lets start resolving:

$1.4\rightarrow\lnot A\lor\lnot B$
$(1.4).2\rightarrow D\lor\lnot B$
$((1.4).2).3\rightarrow D\lor E$
$(((1.4).2).3).5\rightarrow\lnot F\lor E$
$((((1.4).2).3).5).6\rightarrow\lnot F\lor\lnot F\rightarrow\lnot F$

So we have $\lnot F$ and $F$, hence a contradiction
## Practicality of Resolution

Resolution works by taking the negation of a formula we wish to prove true, and showing that it is **unsatisfiable**. This can be impractical since the worst case involves an exponential number of applications

[[SAT Solving|Sat-solvers]] check whether or not a given formula is satisfiable, whilst a proof system aims to give theorems. But these tasks are strongly linked.

Let $F$ be a propositional formula. If $F$ is satisfiable then there exists a truth assignment making it **true** and hence one making $\lnot F$ **false** and so $\lnot F$ is not a tautology. If $\lnot F$ is not a tautology then there exists some truth assignment making $\lnot F$ **false**, so there exists a truth assignment making $F$ **true**

So $F$ is satisfiable, if and only if $\lnot F$ is not a tautology. This demonstrates the strong link between SAT-solving and automated theorem proving