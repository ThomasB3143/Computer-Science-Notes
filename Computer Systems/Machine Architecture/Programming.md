Section: [[Machine Architecture (Root)]]
## Translating and Starting a Program

- The compiler translates high-level code into assembly language
- The assembler turns assembly code into machine language code
- The linker combines the object file (recently translated machine code) with more machine code (from already compiled and assembled libraries and stuff)
- The loader puts the executable machine code into memory
## Assembler

The assembler makes two passes through the assembly code. The first pass assigns instructions addresses and finds symbols such as labels and global variable names, making a **symbol table** for them. The second pass generates the object file.

The linker creates the executable by combining the object file with other machine language code
## Functions

MIPS functions have **arguments** and a **return value** much like any other function

The "jal" instruction (jump and link) jumps to the address but also stores, in [[Introduction to MIPS#Registers|$ra]], the address where the program needs to return to. Then "jr $ra" is used to jump to the address stored in $ra 

We can move return values into $v0 or $v1 

In MIPS convention, the caller places arguments in registers $a0 to $a3, the return values are placed in registers $v0 or $v1 and the saved registers $s0 to $s7 are not modified by the called function. However, this convention can be restrictive. It is a bit better for the function to save important registers in a stack and restore them before returning to the caller
## Loops

A loop is implemented as a jump instruction with a conditional jump to escape the loop when a condition is eventually met
## Input

The "syscall" instruction suspends program execution to provide a service similar to an OS, like inputs and outputs! We use a code to specify what syscall is doing, here are some examples:

| Service       | Code | arguments | result |
| ------------- | ---- | --------- | ------ |
| print integer | 1    | $a0       |        |
| print string  | 4    | $a0       |        |
| read integer  | 5    |           | $v0    |
| exit          | 10   |           |        |
We can load this code into $v0 to access the service