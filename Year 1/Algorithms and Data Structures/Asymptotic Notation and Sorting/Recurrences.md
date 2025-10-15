Section: [[Asymptotic Notation and Sorting (Root)]]

To start analysing recursive algorithms, we need to note that most of them are hybrids between iterative and recursive. For example, [[Sorting#MergeSort|MergeSort]] is recursive, but contains an iterative function to merge two sorted sub-lists

Let's consider MergeSort further, recall that we:

- Split an input of size $n$ into two halves of size $\frac n2$ each
- Recurse into each half
- Merge the resulting sorted sequences

We can represent the function returning the time taken to carry out MergeSort as $T(n)$ using a piecewise like so:

$T(n)=\begin{cases}d & n\leq c, \text{ for constants }c,d>0\\2T(\frac{n}{2})+an& \text{otherwise}\end{cases}$

the $an$ is the time taken to merge and each of the $T(\frac{n}{2})$ is the time taken to carry out the recursive call. $d$ is the time taken to handle the base case when $n$ has fallen to or below the value of $c$

We have two methods for solving these recurrences, **induction** and the **master theorem**
# Induction

To solve a recurrence by induction, we need to guess the correct solution and verify the base case and step

For example, lets guess that [[Sorting#MergeSort|MergeSort]] is $O(n\log n)$ (it is). We will check that $T(n)\leq \alpha n\log_2n$ for some constant $\alpha > 0$

Lets ignore the case $n=1$ and only consider $n\geq 2$. We first need to consider the values of $n$ within our **base case** of $2\leq n\leq c$

Recall that $T(n)\leq d$ when $n\leq c$ for constants $c$ and $d$. We can say that, when $\alpha$ is large enough:

$d\leq\alpha n\log_2n$ for $2\leq n\leq c\iff\alpha\geq \frac{d}{2\log_22}=\frac{d}{2}$

Then for all $2\leq n\leq c$ we have $T(n)\leq d\leq \alpha n\log_2n$

As for the general case, we can plug in our guess like so:

$T(n)\leq 2T(\frac n2)+ an$
$T(n)\leq 2\alpha\frac n2\log_2\frac n2+ an$
$T(n)\leq 2\alpha\frac n2(\log_2n-\log_22)+ an$
$T(n)\leq 2\alpha\frac n2(\log_2n-1)+ an$
$T(n)\leq \alpha n(\log_2n-1)+ an$
$T(n)\leq \alpha n\log_2n-\alpha n+ an$
$T(n)\leq \alpha n\log_2n$   if $\alpha n\geq an\iff \alpha\geq a$

Altogether it works for any $\alpha\geq \max\{\frac d2,a\}$
# Master Theorem

The master theorem can be used on recurrences in the form:

$T(n)=aT(n/b)+f(n)$

for **constants** $a\geq 1$ and $b>1$ and **non-recursive** function $f(n)$ we have three cases:

1. **If** $f(n)=O(n^{\log_b(a)-\epsilon})$ for some constant $\epsilon>0$ **then** $T(n)=\Theta(n^{\log_ba})$
2. **If** $f(n)=\Theta(n^{\log_b(a)}\log^kn)$ for some constant $k\geq 0$ **then** $T(n)=\Theta(n^{\log_ba}\log^{k+1}n)$
3. **If** $f(n)=\Omega(n^{\log_b(a)+\epsilon})$ for some constant $\epsilon\geq 0$ **and** if $af(n/b)\leq cf(n),c<1$ for all $n$ large enough **then** $T(n)=\Theta(n^{\log_ba}\log^{k+1}n)$