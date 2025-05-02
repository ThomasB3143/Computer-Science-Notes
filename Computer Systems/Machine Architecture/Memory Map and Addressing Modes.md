Section: [[Machine Architecture (Root)]]

In MIPS, a **word** is 32 bits (recall that a byte is 8). This means that MIPS uses 32-bit memory addresses, but memory is **byte addressable**

Hence the MIPS address space spans $2^{32}$ bytes or about 4GB

Word addresses are always divisible by 4 (two least significant bits are 0)

Here is the blessed **memory map**
![[Pasted image 20250329183107.png]]
## Text

This segment stores the machine language program with roughly 256MB of code. The four most significant bits are 0 This is why the [[Introduction to MIPS#J-type|j]] instruction only needs 26 bits to reference a word address
## Global Data

This section stores global variables, accessed using the [[Introduction to MIPS#Registers|$gp]] pointers
## Dynamic Data

This section stores data dynamically allocated and deallocated throughout program execution. It spans nearly 2GB of the address space and stores data in a **stack** and **heap**
## Reserved

This is used by the operating system and cannot be directly accessed by the program
# Addressing Modes
## Register Only

Used by [[Introduction to MIPS#R-type|R-type]] instructions, this mode uses registers for all source and destination operands
## Immediate

Uses registers and a 16-bit immediate value as operands. Only **some** [[Introduction to MIPS#I-type|I-type]] instructions use immediate addressing (depending on how the immediate is used)
## Base Addressing

Used in memory access instructions, implemented by I-type instructions. The address of the memory operand is computed by adding the base in the "rs" register to the 16-bit stored in "imm"

The assembly code "lw $t2, 32 ($0)" is translated as:

| op     | rs    | rt    | imm                 |
| ------ | ----- | ----- | ------------------- |
| 100011 | 00000 | 01010 | 0000 0000 0010 0000 |
## PC-relative Addressing

Branching instructions can reference addresses relative to the position of the PC. Basically, we take the PC value and subtract it from the Branch Target Address. Remember, each instruction is FOUR bytes long (just in case you've forgotten by this point)
## Pseudo-Direct Addressing

In **direct addressing**, we'd specify an address in the instruction. MIPS does not support this, as we would need 32 bits for the address and 6-bits for the address and we only have 32 bits for the whole instruction.

MIPS uses pseudo-direct addressing in [[Introduction to MIPS#J-type|J-type]], calculating the new value of the PC as follows:

- The two least significant bits are 0 (instructions are word aligned and 4 bytes long)
- The next 26 bits are taken from the "addr" field of the J-type instruction
- The four most significant bits are again 0 (recall [[Memory Map and Addressing Modes#Text]])