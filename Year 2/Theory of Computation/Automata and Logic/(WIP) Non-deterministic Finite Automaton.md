#wip Section: [[Automata and Logic (Root)]]

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