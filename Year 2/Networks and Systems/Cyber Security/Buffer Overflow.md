Section: [[Cyber Security (Root)]]
# Memory

A virtual address space, we focus on the **stack** for buffer overflow
# Stack and Stack Frame

The stack holds **stack frames**, which represent a single procedure call. The stack frame has:

- Function arguments
- Local variables
- Info to restore the caller's state

The fact that:

- User data and control flow info share the stack
- Untrusted inputs are copied into a buffer without bounds checking

Can allow local variables to overwrite stack information

