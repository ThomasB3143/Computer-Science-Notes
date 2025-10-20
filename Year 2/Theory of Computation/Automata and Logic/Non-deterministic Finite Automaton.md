Section: [[Automata and Logic (Root)]]

>[!cite] Definition
>A 5-tuple ($Q,\Sigma,\delta,q_0,F$), where
>- $Q$ is a finite set of **states**
>- $\Sigma$ is a finite **alphabet**
>- $\delta:Q\times(\Sigma\cup\{\epsilon\})\mapsto P(Q)$ is the **transition function**
>- $q_0\in Q$ is the **start state**
>- $F\subseteq Q$ is the set of **accept states**

$P(Q)$ is the **power set** of states

![[Pasted image 20251013102005.png]]

This DFA allows us to jump from $q_2$ to $q_3$ without reading the next input, and it also lets us either stay in $q_1$ or go to $q_2$ in $q_1$ read 1! Having the ability to transition without input and have multiple possible transitions for an input is the NFA's source of **non-determinism**.

There can be more than one next possible states (like in $q_1$ read 1) hence we get a funky tree like this for the input $010110$:

![[Pasted image 20251013102415.png]]
Standard convention dictates that a single step in the computation consists of reading the next input followed by taking any number of $\epsilon$-transitions
# Computation of an NFA

A **word** $w$ ,in the language $L$, over $\Sigma$ is **accepted** by Non-deterministic Finite Automata $M$ if there is a sequence of states that end in an **accept state** when the word is input in order. Just like [[Finite State Automata and Regex#Deterministic Finite Automata|DFA's]]! The only difference is that there are multiple sequences of states for a given input, we just need **at least one**.
# Concatenation

Suppose we form a new language $L=L_1\circ L_2$ such that each $w\in L =xy,x\in L_1,y\in L_2$.

We can form this language by running $M_1$ on a prefix of $w$ and then running $M_2$ on the rest. However, this cannot be represented with a [[Finite State Automata and Regex#Deterministic Finite Automata|DFA]].
# Converting NFA into DFA

Let ($Q,\Sigma,\delta,q_0,F$) be our NFA, we can construct our DFA ($Q^\prime,\Sigma,\delta^\prime,q_0^\prime,F^\prime$) like so:

1. $Q^\prime = P(Q)$ so $Q^\prime$ is now the set of all subsets of $Q$
2. For $R\in Q^\prime$ and $a\in\Sigma$ let $\delta^\prime(R,a)=\{q\in Q|q\in E(\delta(r,a))\text{ for some }r\in R\}$
3. $q_0^\prime=E(\{q_0\})$
4. $F^\prime=\{R\in Q^\prime|\exists r\in R,r\in F\}$

Through this method, we get from this:
![[Pasted image 20251013105341.png]]
To this:
![[Pasted image 20251013105400.png]]
We need that empty state to represent sequences that are not defined.
# Equivalence of FA and Regular Expressions

>[!cite] Theorem
>A language is regular if and only if some regular expression describes it

We can easily prove that a NFA can be constructed from any RE, as all initial REs can be implemented by NFAs. Since the class of regular languages is closed under regular operations, all REs correspond to a NFA.

Constructing an RE from a DFA is a bit harder:
# Generalised Non-deterministic Finite Automaton (GNFA)

A GNFA has:

1. A **single start state** with no incoming edges
2. A **single accept state** with no outgoing edges
3. Every transition is labelled with a **regular expression**

To convert a FA into a GNFA, we add these start and end states, then replace the internal states one by one with regular expressions
## Internal State Elimination

Pick an internal state for elimination $r$, then for every two neighbouring states we replace the transition between them with a regular expression that functions identically to that which $r$ provided:
![[Pasted image 20251020092315.png]]
# Non-Regular Languages

We can prove that a language is regular by either constructing a FA that recognises it or producing a regular expression that describes it. Proving that a language is **not** regular requires using an **adversary argument** against the DFA in order to get a **contradiction**

Example: Prove that the language $L=\{a^nb^n|n\in\mathbb{N}\}$ is **not regular**

First we assume that their is a DFA $M$ with $m$ states that recognises $L$. Consider the set of words $S=\{a^n|0\leq n\leq m\}$. There are $m+1$ words in $S$, so there must be two different words $a^i$ and $a^j$ that end up in the same state (there aren't enough states for a unique state per word).

If we continue from this state to make $a^ib^i$ and $a^jb^i$ we end up in the same state. But $a^ib^i\in L$ whereas $a^jb^i\notin L$.

The state is an accept state and a non-accept state at the same time, hence we have our contradiction.
# Pumping Lemma

>[!cite] Lemma
>For every regular language $L$, there is a number $p$ (the pumping length) such that every word of at least length $p$ can be divided into three parts $xyz$ such that:
>1. $xy^iz\in L$ for every $i\in\mathbb{N}$
>2. $y$ is a non-empty string
>3. The length of string $xy$ is not greater than $p$

We prove this lemma using the pigeon hole principle, as any word beyond a certain length must enter the same state twice.