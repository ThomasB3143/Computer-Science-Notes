Section: [[Probability (Root)]]
# Conditional Probability

Suppose two events happen in sequence, $A$ and $B$. Sometimes the outcome of one event will sway the other. The probability of $A$ given $B$ is:
$$P(A|B)=\frac{P(A\cap B)}{{P(B)}}$$
Hence:
$$P(A\cap B)=P(B)P(A|B)$$
# Dependence

Events can occur independently, meaning that the outcome of one will not affect the other. Mathematically, this provides the following relations:
$$P(A\cap B)=P(A)P(B)$$
$$P(A|B)=P(A)$$
# Bayes' Theorem

Bayes' Theorem computes the probability of a condition, given an outcome:
$$Posterior=\frac{Likelihood\times Prior}{Evidence}$$
Which is the same as:
$$P(A|B)=\frac{P(B|A)\times P(A)}{P(B)}$$
## Example of Bayes' Theorem

Problem: 

Box 1 contains 3 red and 2 blue marbles, Box 2 contains 2 red and 8 blue marbles. A coin is tossed to decide which box a marble is removed from.

Given that a red marble is removed, what is the probability that Box 1 was chosen?

Solution:

$R$ = Marble is red
$B_1$ = Box 1 is chosen = $1/2$ 
$B_2$ = Box 2 is chosen = $1/2$

We want $P(B_1|R)$, and:

$$P(B_1|R)=\frac{P(B_1)P(R|B_1)}{P(R)}=\frac{P(B_1)P(R|B_1)}{P(B_1)P(R|B_1)+P(B_2)P(R|B_2)}$$
$$P(B_1|R)=\frac{\frac{1}{2}\times\frac{3}{5}}{\frac{1}{2}\times\frac{3}{5}+\frac{1}{2}\times\frac{2}{10}}=\frac{3}{4}$$