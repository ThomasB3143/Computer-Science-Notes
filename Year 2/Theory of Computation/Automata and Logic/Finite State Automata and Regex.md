Section: [[Automata and Logic (Root)]]
# Deterministic Finite Automata

>[!cite] Definition
>A 5-tuple ($Q,\Sigma,\delta,q_0,F$), where
>- $Q$ is a finite set of **states**
>- $\Sigma$ is a finite **alphabet**
>- $\delta:Q\times\Sigma\mapsto Q$ is the **transition function**
>- $q_0\in Q$ is the **start state**
>- $F\subseteq Q$ is the set of **accept states**

## Acceptance

A **word** $w$ ,in the language $L$, over $\Sigma$ is **accepted** by [[#Deterministic Finite Automata]] $M$ if there is a sequence of states that end in an **accept state** when the word is input in order.
# Regular Language

>[!cite] Definition
>A language that can be recognised by a [[#Deterministic Finite Automata|DFA]]
## Regular Operations

- Boolean (set-theoretic)
	- Union
	- Intersection
	- Difference
	- Complement
- Language Theory Specific
	- Concatenation - $A\circ B=\{xy\;|\;x\in A\text{ and }y\in B\}$
		- We also assume $AB=A\circ B$ 
	- Star - $A^*=\{x_1x_2\dots x_k\;|\;k\geq0\text{ and }x_i\in A\text{ for every }i,1\leq i\leq k\}$
		- Same as $\bigcup\limits^\infty_{i=0}A^i$

The precedence order is $^*,\circ,\cup$
# Regular Expression

>[!cite] Definition
>A **regular expression** (RE) defines a **language**, and are logically equivalent to [[#Deterministic Finite Automata]]. $R$ is a regular expression over alphabet $\Sigma$ if $R$ is:
>- in $\Sigma$
>- An empty string $\epsilon$
>- An empty set $\emptyset$ 
>- The **union** of two REs
>- The **concatenation** of two REs
>- The **star** of a RE

This **recursive** definition accounts for all possible RE's
# Combining Automata

To combine $M_1$ and $M_2$, with their acceptance languages $L_1$ and $L_2$ we run the input in **parallel** to get $M$ where $L=L_1\cup L_2$ and:

1. $Q=Q_1\times Q_2$
2. $\delta((s,u),a)=(\delta_1(s,a),\delta_2(u,a))$ for every $s\in Q_1$ and $u\in Q_2$, $a\in\Sigma$
3. $q_0 = (q_1,q_2)$
4. $F=\{(s,u)\in Q\;|\; s\in F_1\text{ or }u\in F_2\}$

Step 1 is true as we need all pairs of states from both automata.

Step 2 means that we apply the overall transition function to the state of each automaton and their shared input. The new pair of states is determined by what both transition functions would do to their respective input.
