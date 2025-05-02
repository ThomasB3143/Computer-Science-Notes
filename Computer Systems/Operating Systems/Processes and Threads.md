Section: [[Operating Systems (Root)]]
# Processes

A **process** is a program in execution. 

They require resources such as:

- CPU time
- Memory
- Files
- I/O devices

All of which can be allocated at the start/during a process

A process includes:

- Code - The text section
- Current activity - Represented by the program counter and content of CPU registers
- Stack - Temporary data such as local variables
- Data section - Global variables
- Heap - memory allocated in run-time
## Process Control Block

Process information is stored in a **process control block** (PCB), these combine to form a table. Each PCB includes the following:

- Unique identifier
- State
- CPU registers
- CPU scheduling info (such as priority)
- Memory usage
- Miscellaneous info (accounting, I/O status etc)
# Process States

A process can change **state** to the following:

- New - the process is being created
- Running - Instructions are being executed
- Waiting - The process is waiting to be dispatched to the CPU
- Ready - The process is ready to be dispatched to the CPU
- Terminated - The process has been terminated, possibly due to completion

Here is a handy diagram

![[Pasted image 20250222210736.png]]
# Process Creation

A process (or **parent process**) can create **child processes** and so on, forming a tree of processes. With regards to resource sharing there are the following cases:

1. Parent and child share all resources
2. Child shares a subset of parent resources
3. Parent and child share no resources

As for execution, there are two cases. Either the parent and child execute concurrently, or the parent waits until the child terminates

As for address space, the child duplicates that of the parent, to allow for easier communication
# Process Termination

After asking the OS to delete it, a process to be terminated will:

- Output data from child processes to parent
- De-allocate child resources
- Termination of child processes if:
	- One has exceeded its allocated resources
	- A task of one is no longer required
	- The parent is terminating (this cascades down the tree)
# Process Scheduling

To maximise CPU use, processes are quickly switched onto the CPU for time sharing. A **process scheduler** selects among available processes for next execution on the CPU, however in doing so requires:

- Job queue - set of all processes
- Ready queue - Set of all processes in main memory, ready and waiting to execute
- Device queues - Set of processes waiting for an I/O device

It is important to understand that processes migrate between the queues
# Deeper Into the Kernel

Recall the [[Introduction to Operating Systems#The Kernel|kernel]], the aim of the kernel is to provide an environment for processes to exist. To do so it needs:

- [[Introduction to Operating Systems#Privileged Instructions|Privileged instruction set]]
- Interrupt mechanism
- Memory protection
- Real-time clock

The kernel consists of:

- A **first-level interrupt handler** (FLIH) to manage interrupts
	- Determines the source of an interrupt (prioritised)
	- Initiates servicing of the interrupt (dispatcher selects the process needed)
- A **dispatcher/scheduler** to switch between processes
	- Assigns resources to processes
	- Initiated when a process cannot continue
	- Also when the CPU is needed elsewhere, such as when:
		- An interrupt changes the [[Processes and Threads#Process States|process state]]
		- A system call prevents the process from continuing
		- An error suspends the process
- **Intra operating system communications** (such as via the system bus)
# Threads

**Threads** are a unit of execution. They can be **traced** meaning the sequence of instructions executed can be listed.

A thread belongs to a [[Processes and Threads#Processes|process]], and executes within it. The two types are **user threads** and **kernel threads**

In **multithreading**, the OS supports multiple threads per process. Whilst in **single threading**, the OS does not recognise the concept of a separate thread (MS-DOS is a prime example, with one process per thread). In a multithreaded process, each thread will have its own stack and set of registers
## Thread Model

Each thread contains a **stack** and **local variables**, allocated on the stack. **Global variables** are shared between threads, allocated in the **data** section of a process (this makes concurrency control an issue to consider). **Dynamically allocated memory** can be global or local (this is program defined)

Here are some awesome benefits of threads:

- Timing - it takes less time to create, terminate and switch between threads as opposed to processes
- Responsiveness - May allow for continued execution if part of a process is blocked
- Resource sharing - Threads can share the resources of a process, this is much easier than shared memory or memory passing between processes
- Economy - Cheaper than process creation, thread switching is lower overhead than context switching (switching between processes)
- Scalability - A process can easily take advantage of **multiprocessor** architectures
# Concurrency, Parallelism and Amdahl's law 

In a **single-core system**, concurrent execution will occur. Meaning that one thread is carried out at a time, and often paused to work on others. In a **multi-core system** this still occurs in individual cores, however the system can run threads **simultaneously**

**Amdahl's law** identifies performance gains from adding additional cores to an application with both serial and parallel cores. Where $S$ is the serial portion and $N$ is the number of processing cores:

$speedup\leq\frac{1}{S+\frac{(1-S)}{N}}$ 

For example, if an application is 25% serial, moving from 1 to 2 cores results in a speedup of $\frac{1}{0.25+\frac{(1-0.25)}{2}}=1.6$ times.

As $N$ approaches, infinity, speedup approaches $1/S$ 
# Multithreading Models

- Many-to-One:
	- Many user-level threads mapped to a single kernel thread
	- One threading block blocks all others
	- Multiple threads cannot run in parallel on multicore because only one may be in the kernel at a time
- One-to-One
	- Each user-level thread maps to a kernel thread
	- Creation of a user-level thread forms a kernel thread also
	- More concurrency than many-to-one
	- Threads per process restricted due to overhead
	- Linux and Windows use this
- Many-to-Many
	- Allows many user-level threads to be mapped to many kernel threads
	- The operating system can create a sufficient number of threads