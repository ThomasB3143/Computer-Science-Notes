Section: [[CT Term 1 Topic 1 (Root)]]
1.3.1 - Operating Systems 

- Provides interface between programming applications and hardware 
    
- Manages efficient and safe use of a computer's resources 
    
- Uses system calls to organize access to memory by programs 
    
- Kernel 
    
    - Program loaded at boot time 
        
    - Has primary control of the processor 
        
- Functions of an operating system 
    
    - Virtualizing a machine: 
        
        - Provides abstractions to present physical components as a clean, virtual interface 
            
    - Starts and stops programs: 
        
        - Manages the changes in available memory and processor scheduling when this occurs 
            
    - Manages memory: 
        
        - Allocates memory to programs 
            
        - Ensures that the program is able to use the memory given to it instead of the one it requests 
            
    - Handles I/O's: 
        
        - Handles requests from I/O devices such as keyboards and monitors 
            
        - Typically done through interrupts 
            
    - File system maintenance: 
        
        - Ensure programs and users can only access their files, and structures files to be easily accessed 
            
    - Network Handling: 
        
        - Monitors networks for incoming traffic and outputs data packets when requested 
            
    - Security: 
        
        - Restricts access for programs to prevent malicious behavior 
            
    - Error handling: 
        
        - Handles errors within programs to prevent disastrous effects 
            

1.3.2 - Input/Output 

- Uses interrupts for things such as keyboard presses or waiting for them 
    
- The OS lets the CPU focus on other tasks until this interrupt is raised 
    
    - Indicated by the interrupt handler 
        

1.3.3 - Processes 

- Executing programs are called processes 
    
- Consists of a thread/threads and address space 
    
    - Thread – Sequence of instructions 
        
    - Address Space – memory locations accessible by the process 
        
- Threads need to synchronize and not be in the critical section simultaneously 
    
- This is exclusive access to a shared resource 
    

1.3.4 - Process life-cycle 

- States: 
    
    - New – Creating a process 
        
    - Ready – Ready to execute 
        
    - Running – Being executed 
        
    - Blocked – Waiting for an event to continue execution 
        
    - Exit – Finished 
        
- Transitions 
    
    - Admit – Process set up and moved to the run queue 
        
    - Dispatch – Scheduler allocates CPU to a process to execute 
        
    - Time-out/yield - Process releases access to the CPU 
        
    - Event-wait – Process waiting for an input and gives up CPU access 
        
    - Event – event occurred to wake up process 
        
    - Release – process terminates and releases access to resources 
        

1.3.5 - Process Control Block 

- A data structure used by the kernel to manage a process 
    
- Consists of: 
    
    - Unique ID 
        
    - State of process (refer to above) 
        
    - CPU scheduling info like priority 
        
    - PC and other CPU registers (available for non-running processes) 
        
    - Memory management info (like address space location) 
        
    - Accounting info (like last run time and CPU time used so far) 
        
    - Reference to next and previous PCB in the list of them (like a linked list!) 
        

1.3.6 - Context Switching 

- Pausing one process and resuming another 
    
- Very time consuming as the PCB for each process must be managed