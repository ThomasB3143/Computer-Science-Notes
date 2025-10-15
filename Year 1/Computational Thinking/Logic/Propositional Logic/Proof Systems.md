Section: [[Propositional Logic (Root)]]

Remember from our [[Introduction to Logic#Components of a Logic|Intro to logic]] that a proof system must be sound and complete. A proof system is a collection of **rules of inference** that can be applied to infer new formulae from old.

## Arguments

An **argument form** in propositional logic is a sequence of formulae. This argument form is valid if, for any true truth assignment, each formula evaluates to true as well as the argument form itself. That sounds really confusing but it's basically just:

$\psi_1,\psi_2,\dots,\psi_n,\Psi$ such that the rule of inference is  $\psi_1,\psi_2,\dots,\psi_n\implies\Psi$

This can be written in the form of a **sequent**:

$\psi_1,\psi_2,\dots,\psi_n\vdash\Psi$

The rule of inference is a tautology if the above argument form is valid.

This rule of inference is **modus ponens** (the law of detachment)

## Rules
### Modus Ponens

$(a\land(a\implies b))\implies b$
or
$\begin{matrix}a & a\implies b\\\hline b\end{matrix}$
### Modus Tollens

$(\lnot a\land(a\implies b))\implies\lnot b$
or
$\begin{matrix}\lnot a & a\implies b\\\hline\lnot b\end{matrix}$
### Hypothetical Syllogism

$((a\implies b)\land(b\implies c))\implies (a\implies c)$
or
$\begin{matrix}a\implies b & b\implies c\\\hline a\implies c\end{matrix}$
### Resolution

$((a\lor b)\land(\lnot a\lor c))\implies b\lor c$
or
$\begin{matrix}a\lor b & \lnot a\lor c\\\hline b\lor c\end{matrix}$
### $\land$-Introduction / $\land$i

$\begin{matrix}a & b\\\hline a\land b\end{matrix}$
### $\land$-elimination / $\land$e1 / $\land$e2

$\begin{matrix}a\land b\\\hline a\end{matrix}$  or  $\begin{matrix}a\land b\\\hline b\end{matrix}$
### $\lnot\lnot$-Introduction / $\lnot\lnot$i

$\begin{matrix}a\\\hline \lnot\lnot a\end{matrix}$
### $\lnot\lnot$-elimination / $\lnot\lnot$e

$\begin{matrix}\lnot\lnot a\\\hline a\end{matrix}$
### $\implies$-elimination / $\implies$e

$\begin{matrix}a & a\implies b\\\hline b\end{matrix}$ ([[Proof Systems#Modus Ponens|Modus Ponens]] but without the Latin)
### $\implies$-introduction / $\implies$i

$\begin{matrix}a\\ \ldots \\ b\\\hline a\implies b\end{matrix}$ (This is the only way to escape an assumption)
### $\lor$-Introduction / $\lor$i1 / $\lor$i2

$\begin{matrix}a\\\hline a\lor b\end{matrix}$  or  $\begin{matrix}a\\\hline b\lor a\end{matrix}$ (Its easy to turn things into a $\lor$ but hard to turn it into anything else)
### $\lor$-elimination / $\lor$e

$\begin{matrix}&a&b\\&\dots&\dots\\a\lor b &c&c\\\hline c\end{matrix}$  (assume $a$ and get to $c$, assume $b$ then get to $c$)
### $\bot$-elimination / $\bot$e

$\begin{matrix}\bot\\\hline a\end{matrix}$ because if one has a contradiction then one can infer **any** formula
### $\lnot$-elimination / $\lnot$e

$\begin{matrix}a & \lnot a\\\hline\bot\end{matrix}$  This is the law of the excluded middle
### $\lnot$-introduction / $\lnot$i
$\begin{matrix}a\\ \ldots \\ \bot \\ \hline \lnot a\end{matrix}$   like a proof by contradiction
## Natural Deduction

This proof system consists of a collection of **rules of inference** and used to obtain proofs using **premises**. Here is a simple example:

Proving $a,\lnot\lnot(b\land c)\vdash\lnot\lnot p\land c$ :

$\begin{matrix}1. & a & premise\\2. & \lnot\lnot(b\land c) & premise\\3. & \lnot\lnot a & \lnot\lnot i \;1\\4. & b\land c & \lnot\lnot e\;2\\5. & c & \land e2\;4\\6. & \lnot\lnot a\land c & \land i\;3\;5\end{matrix}$

This means that the sequence is **valid** and that if $p$ and $\lnot\lnot(b\land c)$ are true under a truth assignment, then $\lnot\lnot p\land c$ is true under the same truth assignment
## Soundness

if the sequent $a,b,c,d\vdash e$ is provable then $a\land b\land c\land d\implies e$ is a tautology
## Completeness

If $a\land b\land c\land d\implies e$ is a tautology then the sequent $a,b,c,d\vdash e$ is provable 
## Theorems

A theorem is a formula for which a sequent with the formula as the [[Proof Systems#Arguments|argument form]] is provable. This is because the soundness and completeness of natural deduction states that every theorem is a tautology and every tautology is a theorem