Section: [[Operating Systems (Root)]]
# Magnetic Storage

Comprised of rotating discs, with a read/write head to access data stored on it
![[Pasted image 20250406200653.png]]

## Disk Performance Parameters

- Seek time
	- Moving head to the target track
- Rotational delay
	- Time for the target sector to rotate under the head
- Access time
	- Seek time + rotational delay
# Disk Scheduling

The OS is responsible for efficient use of hardware, such as optimising **access time** and thus **disk bandwidth** (the bytes transferred per unit time between the request for a service and its completion)

The OS maintains a **queue** of requests for each disk/device. Idle disks can immediately work on a request, whilst busy disks have a request enqueued. Lets look at some algorithms to optimise these queues:
### First-Come First-Served (FCFS)

Just use a basic queue and handle the requests in the same order they are made
![[Pasted image 20250406201203.png]]
### Shortest Seek Time First (SSTF)

Selects the request with the minimum seek time from the current head position. This can lead to **starvation** as closer requests are made repeatedly, leaving further requests unfulfilled for an inconveniently long time
![[Pasted image 20250406201420.png]]
### SCAN / Elevator

Disk arm starts at one end and scans across to the other, handling requests as their location is passed, then goes back and forth. This seems really good but if requests are unevenly distributed there can be some unfairness
![[Pasted image 20250406201640.png]]
### C-SCAN

Basically [[Storage Management#SCAN / Elevator|SCAN]] but we don't reverse the head movement. We just go around it like a circle. This provides a more uniform wait time than SCAN
### LOOK and C-LOOK

These are versions of SCAN and C-SCAN respectively, where the arm only goes as far as the last request in each direction, then reverses without going to the other end of the desktop
## What to Use???

SSTF is common and easily implemented, whilst SCAN/C-SCAN perform better for systems with a heavy load on the disk (less starvation)

Here is a handy table to understand them all:
![[Pasted image 20250406202222.png]]
## Storage Array

An array of disks, with controllers to provide features to hosts

- Ports connect hosts to the array
- Memory and controlling software
- The disks
- RAID, hot spares, hot swap
- Shared storage -> more efficiency
## Storage Area Network

- Common in large storage environments
- Multiple hosts attached to multiple storage arrays - flexible
![[Pasted image 20250406203313.png]]
Clients access a server connected to a **storage area network**
## Network-Attached Storage
![[Pasted image 20250406203545.png]]
This is storage made available over a network rather than a local connection. This allows a client to remotely attach to file systems.

NFS (network file storage) and CIFS (common internet file storage) are common protocols. 

These are implemented by remote procedure calls between the host and storage, often over TCP or UDP on the IP network
# RAID

The **Redundant Array of Inexpensive/Independent Disk** provides **reliability** via **redundancy**. This improves the performance and reliability of a system

It is implemented by mirroring or shadowing to keep duplicates of each disk, or through block interleaved parity to use much less information for an equivalent effect
### RAID Levels

We have six RAID levels:

- RAID 0 - Non-redundant striping
- RAID 1 - Mirrored disks
	- RAID (0+1) - Write data in the form of data striping then mirror
	- RAID (1+0) - Mirror and then stripe
	- Latter is better
- RAID 2 - Memory- style error-correcting codes
	- Requires less redundant data than RAID 1, with the same effect
- RAID 3 - bit-interleaved parity
- RAID 4 - block-interleaved parity
- RAID 5 - block-interleaved distributed parity
- RAID 6 - P + Q redundancy