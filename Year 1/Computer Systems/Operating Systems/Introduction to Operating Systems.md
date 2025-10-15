Section: [[Operating Systems (Root)]]

An **operating system** is a program that acts as an intermediary between a user and the hardware. It aims to:

- Execute programs
- Aid in solving user-problems
- Provide convenient use of the computer system
- Use resources fairly and efficiently

To be more specific, the operating system carries out:

- Resource management
- Process management
- Memory management
- Mass storage management
- File system management
- Cache management
- I/O system management
## An Abstract machine

The OS is an **abstract machine** that extends the basic hardware with added functionality.

It can provide **high level abstractions** to be more programming-friendly and is a common core for most applications. It can also make application code more portable by hiding details of the hardware
## A Resource Manager

The OS is also a **resource manager**, responsible for allocating resources to users and processes. It needs to ensure fair progress and allocates on some policy to ensure fairness and efficiency
## The Control Program

The OS controls the execution of user programs and operations of the input and output devices to prevent errors
## The Kernel

The one program that runs at all times
# Structure
### Hardware

This provides basic computing resources such as CPU, memory and I/O devices
### Operating System

This controls and coordinates use of hardware amongst applications and users
### Application Programs

These define the ways in which system resources are used to solve the user's computing problems. Things such as word processors or video games can be found here
### Users

That's us!!
## Privileged Mode

The OS runs in **privileged mode**, meaning that it contains fundamental functionality such as whatever is required to implement other services and provide security.

No application can bypass the operating system, this ensures that it can enforce resource allocation
## Dual-Mode

**Dual mode** allows the OS to protect itself and other components, and is referring to **user mode** and **kernel mode**

A **mode bit** is provided by hardware, providing the ability to distinguish when the system is running user code or kernel code.

Some instructions will be [[Introduction to Operating Systems#Privileged Instructions|privileged]] such that they can only run in kernel mode. A **system call** can [[Introduction to Operating Systems#Switching Modes|switch the mode]] to kernel and a **return from call** sets it back to user
## Privileged Instructions

Some instructions are part of the **privileged instruction set** such as:

- Managing interrupts
- Performing I/O
- Halting processes
## Switching Modes

Switching mode occurs in the following cases:

- A user process calls on the OS to execute a function
- An interrupt occurs
- An error is met in a user process
- A privileged instruction is attempted in user mode
## Operating System Types

- Multi-user
- Multi-programming supports running a program on more than one CPU
- Multi-tasking allows concurrent running of programs
- Multi-threading allows for different parts of a program to run concurrently
- Real-time can respond to inputs instantly
## Operating System Services

These provide an environment for execution of programs. One set provides the essentials:

- A user interface
- The ability to actually execute programs
- I/O operations 
- File-system manipulation to allow programs to search, read from and write to files
- Communications to allow processes to exchange information
- Error detection to be aware of errors in hardware, programs, the CPU or I/O devices

Another set of functions ensures efficiency:

- Resource allocation to distribute resources fairly amongst processes. This can include CPU cycles, main memory, file storage and more
- Accounting to keep track of how much each process/user uses in terms of resources
- Security to control the access of resources amongst users
# User Operating System Interfaces
### CLI

The **command interpreter** allows direct command entry, this is implemented by either the kernel or system programs.

There exist multiple flavours known as **shells**. The command interpreter basically fetches a command from the user and executes it, whether it be built in or the name of a program
### GUI

A **graphical user interface** is a more user-friendly desktop interface, typically utilising a mouse, keyboard and monitor to display and take in information.

It is important to note that most OS include both CLI and GUI
# Operating System Structure
### Simple Structure

These do not have well-defined structures and are small, simple and limited. Furthermore interfaces and levels of functionality are not well separated. MS-DOS is a prime example of this

Fewer interfaces does lead to better performance, however a lack of clear boundaries between modules leads to a complicated structure
### Monolithic

With a single file and single address space, monolithic OS are a step above [[Introduction to Operating Systems#Simple Structure|simple]] in terms of complexity. All OS services are combined into a single code block. UNIX is a good example of this structure type

These have a great performance, as communication between components is quick, and they are much easier to build. However maintenance is difficult, since a small error can affect the entire system
### Microkernel

These move as much from the kernel into the user space by removing all non-essential components and replacing them with system and user programs. MAC OS is a wonderful example

This is great because new services can be added to the user space and don't require the kernel to be modified. This also creates a more reliable OS, as failure of a service does not affect the rest of the operating system

