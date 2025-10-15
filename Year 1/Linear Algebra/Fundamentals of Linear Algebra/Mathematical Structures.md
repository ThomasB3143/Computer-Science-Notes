Section: [[Fundamentals of Linear Algebra (Root)]]
## Groups

A group has a set $G$, a binary operation $*$ and some axioms

- $*$ is closed on $G$ so $*:G\times G\rightarrow G$
- $*$ is associative so $a(b*c)=(a*b)*c$
- There exists an identity element $e\in G\mid\forall a\in G,a*e=e*a=a$
- $*$ has an inverse operator so $\forall a\in G,\exists b\in G\mid a*b=b*a=e$

Some examples of groups include:

- Real numbers with +
- Integers with +
- Rational numbers with $*$
	- NO
	- Because $0$ does not have an inverse operator to get the identity element
## Fields

A field has a set $F$, and two binary operators, typically denoted $+$ and $*$ which we call "addition" and "multiplication"

- Addition and Multiplication must be **associative** so $a+(b+c)=(a+b)+c$ and $a*(b*c)=(a*b)*c$ 
- Addition and Multiplication must be **commutative** so $a+b=b+a$ and $a*b=b*a$ 
- Multiplication over addition must be **distributive** so $a*(b+c)=(a*b)+(a*c)$
- There must be an **additive identity** $0$ in $F$ such that $a+0=a$
- For all $a\in F$, there exists an **additive inverse** $-a\in F$ such that $a+(-a)=0$
- There must be a **multiplicative identity** $1$ in $F$ such that $a*1=a$
- - For all $a\in F,a\neq 0$, there exists a **multiplicative inverse** $a^{-1}\in F$ such that $a*a^{-1}=1$
