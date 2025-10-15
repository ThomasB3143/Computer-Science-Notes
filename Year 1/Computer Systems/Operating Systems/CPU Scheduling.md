Section: [[Operating Systems (Root)]]
# Multiprogramming

Aim is to **maximise** CPU usage by keeping several processes in memory concurrently. When a process is waiting, the OS executes another process in the ready queue.
## Schedulers

- Long-term scheduler
	- Selects processes to be brought into the ready queue
- Medium-term scheduler
	- Is a part of swapping and in charge of handling swapped out processes
- Short-term scheduler
	- Selects the process to be executed next and allocated to the CPU
## Dispatcher

The dispatcher gives control of the CPU to the process selected by the [[CPU Scheduling#Schedulers|scheduler]]. It can:

- Switching context (changing processes)
- Switching to [[Introduction to Operating Systems#Users|user-mode]]
- Jumping to the correct location in the user program to **restart** the program

Note that the **dispatch latency** is the time taken for the dispatcher to stop a process and start another
## Optimisation Criteria

- Max CPU utilisation
	- Keeping the CPU as busy as possible
- Max throughput
	- The number of processes completing execution per unit time
- Min turnaround time
	- Time taken to execute a given process (waiting time + execute + I/O)
- Min waiting time
	- Total amount of time a process has been waiting in the ready queue
- Min response time
	- The time between a request being submitted and its first response

There are many scheduling algorithms to do this...
### First Come, First Served (FCFS)

The first process requested is the allocated until completion, essentially being placed into a simple FIFO queue

Advantages:

- Simple to implement

Disadvantages:

- Convoy effect, short processes waiting on a long process to finished
## Shortest-Job-First (SJF)

Links each process with the length of its next CPU burst and schedule the process with the shortest time (if two are equal use FCFS). It is not **pre-emptive** meaning once CPU time is given to a process it is done so to completion of the burst

Advantages:

- Simple implementation
- Minimum average

Disadvantages:

- Difficult to know the length of the next CPU request
## Shortest Remaining Time First (SRTF)

If a new process arrives in the ready queue with a CPU burst length less than the remaining time of executing processes, then pre-empt the running process and run the process with the shorter CPU burst length

Advantages:

- Again easy to implement

Disadvantages:

- A LOT of context switching (takes time)
## Round Robin (RR)

Each process is given a small, equal unit of CPU time (the **time quantum**), then pre-empted and enqueued. If the time quantum is too large then its basically [[CPU Scheduling#First Come, First Served (FCFS)#|FCFS]], if too small then there is too much context switching. As a good rule of thumb, **80%** of the CPU bursts should be shorter than the time quantum
## Priority Scheduling

Each process is given a priority number (integer) and the CPU is allocated to the process of highest priority. This can be **pre-emptive** or **non pre-emptive**

This raises the issue of **starvation**, where low priority processes may never execute. We can fix this by increasing priority of a process as time goes on. We can combine this with [[CPU Scheduling#Round Robin (RR)|RR]] to execute the highest priority process and use RR on all processes of the same priority
## Multilevel Queue

The **ready** queue is split into separate queues such as **foreground** and **background**, each with its own scheduling algorithm. Scheduling is undertaken between queues (such as serving all from foreground then from background)

Each queue is given a **time slice**, that being a proportion of CPU time

Unfortunately this does not move processes between queues
## Multilevel Feedback Queue

These CAN move processes between queues, allowing for ageing 