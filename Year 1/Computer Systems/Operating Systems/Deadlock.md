Section: [[Operating Systems (Root)]]

A set of processes is **deadlocked** when each process in the set is waiting for an event only another process in the set can cause
# System Model

A system consists of resources:

- Resource types $R_1,R_2,\dots,R_m$
	- CPU cycles, memory space, I/O devices
- Each resource type has $W_i$ instances
- Each process utilises a resource like so:
	- Requests
	- Uses
	- Releases
## Characterising Deadlock

- **Mutual exclusion** - only one process at a time can use a resource
- **Hold and wait** - a process is holding at least one resource, and waiting to acquire additional resources held by other processes
- **No pre-emption** - a resource can be released only voluntarily by the process holding it
- **Circular wait** - There exists a set of waiting resources such that each resource is waiting on another resource in a way that forms a cycle

When all four of these arise, deadlock CAN occur

# Resource-Allocation Graph

A set of vertices $V$ and edges $E$. $V$ is partitioned into both **processes** and **resources**. $E$ is partitioned into **request edges** (between a process and resource to show that the process is requesting the resource) and **assignment edges** (showing that the process is assigned to the resource)
![[Pasted image 20250406211039.png]]
Here we can see that $P_i$ is requesting an instance of $R_j$, of which it has **four**
![[Pasted image 20250406211125.png]]
In this case, $P_i$ is holding an instance of $R_j$

Here is is a RAG for a system:
![[Pasted image 20250406211253.png]]
We have no cycles, hence no deadlock

Now check this example out:
![[Pasted image 20250406211459.png]]
This will result in a deadlock, shown by the cycles highlighted. There are no **safe sequences** that result in all processes being completed
![[Pasted image 20250406211654.png]]
Here, $P_4$ or $P_2$ can be completed to allow all processes to execute. An example safe sequence would be $P_4,P_3,P_1,P_2$

The presence of a cycle is a necessary and sufficient condition for deadlock ONLY when resources have ONE INSTANCE
# Basics

- If a graph contains no cycles, then we have no deadlock
- If a graph contains a cycle:
	- Definitely deadlock if we have one instance per resource types
	- *Maybe* deadlock if not (find a safe sequence to prove it)
# Handling Deadlocks

1. Ignore the problem
2. Prevent deadlock
	1. Negate one of the four [[Deadlock#Characterising Deadlock|necessary conditions]]
3. Avoidance
	1. Careful resource allocation
4. Detect deadlock and recover
### Approach 1 - The Ostrich Algorithm

It is crucial to note that ostriches do not bury their head in the sand to ignore problems. They do it to rotate their eggs they buried in the sand so they cook evenly, much like the function of a spinning plate in a microwave.

Pretending there is no problem is reasonable if deadlocks occur rarely and/or the cost of prevention is high. UNIX and Windows take this approach since resources are plentiful and deadlocks are handled by rebooting anyhow.

We are trading convenience for correctness
### Approach 2 - Deadlock Prevention

**Mutual Exclusion** is not required for sharable resources. For non-sharable resources, it must hold

**Hold and wait** can be eliminated, by ensuring that a process is not holding resources whilst it is requesting another resource. We can do this by requiring a process to request and be allocated all of its resources **before** execution, or by only allowing a process to request when it is not holding resources already. These can result in low resource utilisation and **starvation**

**No pre-emption** can be removed. If a process is holding resources and wants more, then all other resources being held are released and added to a list for which it is waiting. The process only restarts once it can regain its own resources and the new ones it is requesting

**Circular wait** can be removed by imposing an ordering of the resource types. We then require that each process requests resources in an increasing order of enumeration. This removes our cycles
## Approach 3 - Deadlock Avoidance

Requires the system to have **priori information** available:

- Simplest and most useful model require each process to declare a maximum number of resources of each type that it may need
- The deadlock-avoidance algorithm examines the resource-allocation state to ensure there can never be a circular-wait condition
- Resource-allocation state is defined by the number of available and allocated resource, and the maximum demands of the processes
# Safe State

When a process requests a resource, the system must decide if immediate allocation leaves the system in a **safe state**

The system is in a safe state if there exists a sequence of all the process $P_1,P_2,\dots,P_n$ such that, for each $P_i$, the resources the process can request can be satisfied by currently available resources and resources held by all $P_j,j<i$. This follows the reasoning below:

- If $P_i$ has resource needs not immediately available, then it can wait until all $P_j$ have finished
- When $P_j$ is finished, $P_i$ can obtain the resources needed. Then it can execute and terminate, returning the resources
- When $P_i$ terminates, $P_{i+1}$ can obtain its resources and so on

In this state, there are NO deadlocks. Otherwise there MAY be a deadlock
# Avoidance Algorithms

When we have single instances of each resource type, we can use a [[Deadlock#RAG Scheme|resource-allocation graph]]

Otherwise, we use the [[Deadlock#Banker's Algorithm|banker's algorithm]]
### RAG Scheme

We add some new types of edges to our RAG:

- **Claim edge** - $P\rightarrow R$ indicates that process $P$ may request $R$, we use a **dashed** line to show this
- Claim edge converted to a **request edge** when a process requests a resource
- Request edge converted to an **assignment edge** when the resource is allocated to the process
- When the resource is released by a process, the assignment edge is reverted to a **claim edge**
- Resources must be claimed a **priori** in the system
![[Pasted image 20250408163523.png]]
Suppose that a process requests a resource. The request can only be granted if converting the request edge to an assignment edge does not result in the formation of a cycle in the RAG
### Banker's Algorithm

For this, we need the **priori** of the [[Deadlock#Deadlock Avoidance|maximum use]] of each resource for any given process. A process may have to wait and, when it has all of its resources, it must return them in a finite amount of time

Where there are $n$ processes and $m$ resource types, we define the following matrices:

- **Available** - vector of length $m$. If the element of row $i = k$ then there are $k$ instances of resource type $R_i$ available
- **Max** - $n\times m$ matrix. If the element of the $i^{th}$ row and the $j^{th}$ column is $k$, then process $P_i$ may request at most $k$ instances of resource type $R_j$
- **Allocation** - $n\times m$ matrix.  If the element of the $i^{th}$ row and the $j^{th}$ column is $k$, then process $P_i$ is currently allocated $k$ instances of resource type $R_j$
- **Need** - $n\times m$ matrix.  If the element of the $i^{th}$ row and the $j^{th}$ column is $k$, then process $P_i$ needs $k$ instances of resource type $R_j$ to complete its task

$Need=Max-Allocation$
![[Pasted image 20250408170327.png]]
### Banker's Safety Algorithm

1. Let $Work$ and $Finish$ be vectors of length $m$ and $n$ respectively. Initialise:
	- $Work=Available$
	- $Finish[i]=false$ for all $i$ in $Finish.length$
2. Find an $i$ such that both:
	- $Finish[i]=false$
	- $Need_i\leq Work$
	- If no such $i$ exists, go to step 4
3. After step 2:
	- $Work = Work+Allocation_i$
	- $Finish[i]=true$
	- Go to step 2
4. If all $Finish[i]=true$ then the system is in a [[Deadlock#Safe State|safe state]]

The order in which you find $i$ values will be the order of execution that is allowed for the system
### Banker's Resource-Request Algorithm

Define $Request_i$ as a **request vector** for process $P_i$. If $Request_i[j]=k$ then process $P_i$ wants $k$ instances of resource type $R_j$

1. If $Request_i\leq Need_i$ then go to step 2. Otherwise raise an error condition (process has exceeded its maximum claim)
2. If $Request_i\leq Available$ then go to step 3. Otherwise $P_i$ must wait (the resources aren't available)
3. Pretend to allocate the resources to $P_i$ like so:
	1. $Available=Available-Request_i$
	2. $Allocation_i=Allocation_i+Request_i$
	3. $Need_i=Need_i-Request_i$
	4. If in a [[Deadlock#Safe State|safe state]] then allocate the resources for real. Otherwise $P_i$ must wait, and we revert our changes

Basically, when you can assign something, check if it leads to a safe state. If it doesn't, then wait
## Approach 4 - Recovering From Deadlock

Process termination:

- Abort all deadlocked processes
- Abort one at a time until the deadlock cycle is eliminated
- In what order do we abort?
	- Priority of process
	- How long it has computed, and how much longer until completion
	- Resources the process has used
	- Resources the process needs
	- How many processes will need to be terminated