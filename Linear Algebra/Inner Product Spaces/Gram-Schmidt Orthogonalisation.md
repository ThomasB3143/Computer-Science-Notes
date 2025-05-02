Section: [[Inner Product Spaces (Root)]]
## Orthogonal and Orthonormal Sets

A set of vectors is [[Introduction to Inner Product Spaces#Orthogonality|orthogonal]] if all pairs of distinct vectors in it are orthogonal. An orthogonal set consisting of unit vectors is called **orthonormal**

An orthogonal set is also [[Vector Spaces and Linear Combinations#Linear Independence|linearly independent]] and can be treated as a [[Vector Spaces and Linear Combinations#Basis|basis]] 

Where $S=\{v_1,\cdots,v_n\}$ is an orthogonal basis in inner product space $V$, then for any $u\in V$:

$u=\frac{\langle u,v_1\rangle}{||v_1||^2}v_1+\frac{\langle u,v_2\rangle}{||v_2||^2}v_2+\cdots+\frac{\langle u,v_n\rangle}{||v_n||^2}v_n$

Furthermore, if $S$ is an **orthonormal** basis then:

$u=\langle u,v_1\rangle v_1+{\langle u,v_2\rangle}v_2+\cdots+{\langle u,v_n\rangle}v_n$

We can prove this because $u=c_1v_1+c_2v_2+\cdots+c_nv_n$ and $\langle u,v_i\rangle=c_i\langle v_i,v_i\rangle=c_i||v_i||^2$ so $c_i=\frac{\langle u,v_i\rangle}{||v_i||^2}$ 
## Orthogonal Projections

Recall [[Introduction to Inner Product Spaces#Orthogonal Complements|orthogonal complements]] 

The **projection theorem** states that if $W$ is a subspace in a finite-dimensional inner product space $V$ then every vector $u\in V$ can be **uniquely** represented as $u=w_1+w_2$ where $w_1\in W,w_2\in W^\bot$

In this case, $w_1$ is the **orthogonal projection** of $u$ onto $W$ and we write this as $w_1=proj_wu$ and $w_2=proj_{w^\bot}u$

We can compute the orthogonal projection using similar ideas to earlier:

If $\{v_1,\dots v_r\}$ is an orthogonal basis for $W$ and $w_1=c_1v_1+c_2v_2+\dots+c_rv_r$ then we can use $\langle u,v_i \rangle=\langle w_1+w_2,v_i\rangle=\langle w_1,v_i\rangle+\langle w_2,v_i\rangle$ 

But we know that $w_2\in W^\bot$ and $v_i\in W$ hence $\langle w_2,v_i\rangle=0$ 

$\langle u,v_i \rangle=\langle w_1,v_i\rangle=c_i\langle v_i,v_i\rangle=c_i||v_i||^2$  

Hence we can find substitute for all $c_i$ like so:

$proj_wu=\frac{\langle u,v_1\rangle}{||v_1||^2}v_1+\frac{\langle u,v_2\rangle}{||v_2||^2}v_2+\cdots+\frac{\langle u,v_n\rangle}{||v_n||^2}v_n$ 
## The Gram-Schmidt Process

This is used to find an [[Norms and Dot Product#Orthonormality|orthonormal]] basis for a non-zero finite-dimensional inner product space $V$ (every one has it)

- Let $W$ be a subspace of $V$ with basis $\{u_1,\dots u_n\}$ 
- Consider the subspaces of $W$ in the form $W_r=span(u_1,\dots,u_r)$ where $r=1,\dots n$ 
- We know that $W_1\subseteq W_2\subseteq\dots\subseteq W_n=W$
- The **Gram-Schmidt process** inductively constructs orthogonal bases for the subspaces $W_i$ until one is constructed for $W_n=W$
- With an orthogonal basis for $W$ we can just normalise them to get an **orthonormal** basis once the orthogonal basis is formed
### Gram-Schmidt Process Steps

 Step 1:
	let $v_1=u_1$, it is obvious that $v_1$ is an orthogonal basis for $W_1=span(u_1)$

Step $r$:
	If $\{v_1,\dots,v_{r-1}\}$ is an orthogonal basis for $W_{r-1}=span(u_1,\dots,u_{r-1})$, we need to find a vector $v_r$ such that  $\{v_1,\dots,v_{r-1},v_r\}$ is an orthogonal basis for $W_r$

To complete step $r$ we need to use the [[Gram-Schmidt Orthogonalisation#Orthogonal Projections|projection]] theorem from before on $u_r\in W_r$ and $W_{r-1}$ (as a subspace of $W_r$) like so:

$u_r=proj_{W_{r-1}}u_r+proj_{W_{r-1}\bot}u_r$ 

But $\{v_1,\dots,v_{r-1}\}$ is an orthogonal basis for $W_{r-1}$, so we know that:

$proj_{W_{r-1}}u_r=\frac{\langle u_r,v_1\rangle}{||v_1||^2}v_1+\frac{\langle u_r,v_2\rangle}{||v_2||^2}v_2+\cdots+\frac{\langle u_r,v_{r-1}\rangle}{||v_{r-1}||^2}v_{r-1}$

$v_r=proj_{W_{r-1}^\bot}u_r=u_r-\frac{\langle u_r,v_1\rangle}{||v_1||^2}v_1-\frac{\langle u_r,v_2\rangle}{||v_2||^2}v_2-\cdots-\frac{\langle u_r,v_{r-1}\rangle}{||v_{r-1}||^2}v_{r-1}$

Since $v_r\in W^\bot_{r-1}$, the set $\{v_1,\dots,v_{r-1},v_r\}$ is orthogonal (and thus linearly independent) 

Example - Find the orthonormal basis of $W=span(u_1,u_2,u_3)$ where $u_1=(1,1,1)$, $u_2=(0,1,1)$ and $u_3=(0,0,1)$

Firstly we know $v_1=u_1=(1,1,1)$

$v_2=u_2-proj_{W_1}u_2=u_2-\frac{\langle u_2,v_1\rangle}{||v_1||^2}v_1$

$v_2=(0,1,1)-\frac{0\cdot1+1\cdot1+1\cdot1}{1^2+1^2+1^2}(1,1,1)=(0,1,1)-\frac23(1,1,1)=(-\frac23,\frac13,\frac13)$

$v_3=u_3-proj_{W_2}u_3=u_3-\frac{\langle u_3,v_1\rangle}{||v_1||^2}v_1-\frac{\langle u_3,v_2\rangle}{||v_2||^2}v_2$

$v_3=(0,0,1)-\frac{0\cdot1+0\cdot1+1\cdot1}{1^2+1^2+1^2}(1,1,1)-\frac{0\cdot-\frac23+0\cdot\frac13+1\cdot\frac13}{\left(-\frac{2}{3}\right)^2+\left(\frac{1}{3}\right)^2+\left(\frac{1}{3}\right)^2}\left(-\frac23,\frac13,\frac13\right)$

$v_3=(0,0,1)-\frac13(1,1,1)-\frac12\left(-\frac23,\frac13,\frac13\right)=\left(0,-\frac12,\frac12\right)$



