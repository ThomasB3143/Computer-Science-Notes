Section: [[Fundamentals of Calculus (Root)]]
# Sets and Notation

>[!quote] Definition
>A **set** is an unordered collection of distinct objects or **elements**, denoted by $\lbrace\rbrace$

We can build a set like so:

$A=\lbrace a\in animals:a \text{ has a backbone}\rbrace$

Where $:$ or $|$ means "such that"
>[!quote] Definition
>A **tuple** is an **ordered** collection of elements, denoted by $()$

## Union

The **union** of $A$ and $B$ is $A\cup B$ and includes all elements from $A$ **or** $B$
## Intersection

The **intersection** of $A$ and $B$ is $A\cap B$ and includes all elements found in **both** $A$ and $B$
## Inclusion-Exclusion

If $A$ and $B$ are finite sets, then $|A\cup B|=|A|+|B|-|A\cap B|$
## Set Minus

$A\setminus B$ includes the set of all elements from $A$ that are not in $B$
## Powerset

The **powerset** of $A$ (denoted $\wp(A)$ ) is the set of all [[#Subsets|subsets]] of $A$ 
## Cartesian Product

The **cartesian product** of $A$ and $B$ ( $A\times B$ ) is the set of ordered pairs with first element from $A$ and second element from $B$
![[Pasted image 20250502110201.png]]
# Subsets

Let $A$ and $B$ be sets. $A$ is a **subset** of $B$ (denoted $A\subseteq B$) if **every** element of $A$ is in $B$

$A$ is a **proper subset** of $B$ (denoted $A\subset B$) if $A\subseteq B$ and $A\neq B$
# Important Sets
##### The Empty Set
$\emptyset$ contains no elements
##### Natural Numbers
$\mathbb{N}=\lbrace0,1,2,3,4,\dots\rbrace$
##### Integers
$\mathbb{Z}=\lbrace\dots,-2,-1,0,1,2,\dots\rbrace$
##### Rational Numbers
$\mathbb{Q}=\lbrace m/n:m,n\in\mathbb{Z},n\neq0\rbrace$
##### Real Numbers
Includes numbers with infinite decimal expansion like $\pi$
##### Complex Numbers
$\mathbb{C}=\lbrace a+bi:a,b\in\mathbb{R}\rbrace$
# Intervals

- Closed Interval
	$[a,b]=\lbrace x\in\mathbb{R}:a\leq x\leq b\rbrace$  
- Open Interval
	$(a,b)=\lbrace x\in\mathbb{R}:a< x< b\rbrace$
- Half-Open Interval
	$[a,b)=\lbrace x\in\mathbb{R}:a\leq x< b\rbrace$
# Functions

A **function** $f:A\mapsto B$ is an assignment of a unique element of $B$ to every element of $A$. For example, $f:\mathbb{N}\mapsto\mathbb{N}$ where $f(n)=n^2+3$
# Function Composition

Suppose that $f:A\mapsto B$ and $g:B\mapsto C$ are [[#Functions|functions]], we can define the **composition** of $g$ and $f$ as $g\circ f:A\mapsto C$ or $gf:A\mapsto C$ where $g\circ f(x)=g(f(x))$
# Mappings
## Injection

A function $f:A\mapsto B$ is an **injection** if for all $a,b\in A$ if $f(a)=f(b)$ then $a=b$
## Surjection

The function is a **surjection** if for all $b\in B,\exists a\in A$ such that $f(a)=b$ 

Essentially we can map a value from $A$ to any of $B$
## Bijection

A function is **bijective** if it is both [[#Injection|injective]] and [[#Surjection|surjective]]
# Inverse Functions

For a function $f:A\mapsto B$ the **inverse function** $f^{-1}:B\mapsto A$ is such that if $f(a)=b$ then $f^{-1}(b)=a$ 

The inverse of a function only exists when it is [[#Bijection|bijective]]
## Finding the Inverse

To find the inverse, we rewrite the function using $y$ as the unknown and set the function equal to $x$. Then we rearrange the function to make $y$ the subject and write the function using inverse notation

Example - find the inverse of $f(x)=5x+3$

1. $5y+3=x$
2. $5y=x-3$
3. $y=\frac{x-3}{5}$
4. $f^{-1}=\frac{x-3}{5}$
# Cardinality

>[!quote] Definition
>The **cardinality** of a set is the number of distinct elements

Two sets have the same **cardinality** if there is a [[#Bijection|bijection]] between them
## (Un)countably Infinite

For an **unbounded** set with **infinite** cardinality, we say it is **countably infinite** if there is a bijection between the set and [[#Natural Numbers|the set of natural numbers]]. Otherwise it is **uncountably infinite**
