Section: [[Discrete Term 1 (Root)]]
## Induction

Each integer $n$ is associated to a proposition $P(n)$, where $P(n)$ could be something like $2^n>2n$. Prove that it is true for one particular case of $n$, then prove that if it is true for any given $n$, it is true for $n+1$

Example - Prove that $2^n>2n$ for $n\geq3$

When $n=3,2^n=8,2n=6\therefore 2^n>2n$ and $P(3)$ is proven. Now we can prove that $P(n+1)$ holds true when $P(n)$ is assumed true:

$P(n+1):2^{n+1}>2(n+1)$

But $2^{n+1}=2\times2^n>2\times2n$ using the fact that $P(n)$ is true

Now $2\times2n>2(n+1)$ when $n\geq3$, therefore if $P(n)$ is true, $P(n+1)$ is true
$P(3)$ is true therefore $P(4)$ is true and so on
## Pigeon-hole principle

Basically if you need to assign $m$ labels to $n$ entities, if $n>m$ then at least one label will be assigned to more than one entity
## Inclusion-Exclusion principle

Used to find the size of a union of sets, it can be represented as the following equation and you can assume the pattern that applies to a union of more than 3 sets:

$\lvert A\cup B\cup C \rvert = |A|+|B|+|C|-|A\cap B|-|A\cap C|-|B\cap C|+|A\cap B\cap C|$
Example - How many integers in the set $\{1,2,3\dots,210\}$ are divisible by none of 2, 3, 5 and 7?

Let $A_i$ be the set of integers that are not divisible by $i$

$|A_2|=210-210/2=105$   $|A_3|=210-210/3=140$   $|A_5|=210-210/5=168$    $|A_7|=210-210/7=180$   $|A_2\cap A_3|=210-210/6=175$   $|A_2\cap A_5|=210-210/10=189$   $|A_2\cap A_7|=210-210/14=195$   $|A_3\cap A_5|=210-210/15=196$   $|A_3\cap A_7|=210-210/21=200$   $|A_5\cap A_7|=210-210/35=204$   $|A_3\cap A_5\cap A_7|=210-210/105=208$   $|A_2\cap A_5\cap A_7|=210-210/70=207$   $|A_2\cap A_3\cap A_7|=210-210/42=205$   $|A_2\cap A_3\cap A_5|=210-210/30=203$   $|A_2\cap A_3\cap A_5\cap A_7|=210-210/210=209$

Use the inclusion exclusion formula to get $48$!!!
