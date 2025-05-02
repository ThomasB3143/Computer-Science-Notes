Section: [[Machine Architecture (Root)]]

**M**icroprocessor without **I**nterlocked **P**ipeline **S**tages
Follows these principles:

- Simplicity favours regularity
- Make the common case fast
- Smaller is faster
- Good design demands good compromises

We will be focusing on the 32-bit RISC processor, sporting:

- 32-bit words
- ~110 instructions
- 32 general purpose registers
# Registers

| Name      | Number | Use                     |
| --------- | ------ | ----------------------- |
| $0        | 0      | The constant 0          |
| $at       | 1      | assembler temporary     |
| $v0 - $v1 | 2-3    | Function return values  |
| $a0 - $a3 | 4-7    | Function arguments      |
| $t0 - $t7 | 8-15   | Temporary variables     |
| $s0 - $s7 | 16-23  | Saved variables         |
| $t8 - $t9 | 24-25  | Temporary variables     |
| $k0 - $k1 | 26-27  | OS temporaries          |
| $gp       | 28     | Global pointer          |
| $sp       | 29     | Stack pointer           |
| $fp       | 30     | Frame pointer           |
| $ra       | 31     | Function return address |
# MIPS assembly

In MIPS, there are three types of instructions
## R-type

| op  | rs  | rt  | rd  | shamt | funct |
| --- | --- | --- | --- | ----- | ----- |
| 6   | 5   | 5   | 5   | 5     | 6     |
- op - the **opcode**, always 0 for R-type
- rs and rt - the **source registers**
- rd - the **destination register**
- shamt - the **shift amount** for shift instructions, otherwise 0
- funct - the **function**, the second part of the opcode. The op being 0 implies the instruction is an R-type, the funct specifies which R-type instruction it is

For example, "add $s0, $s1, $s2" translates to:

| op     | rs    | rt    | rd    | shamt | funct  |
| ------ | ----- | ----- | ----- | ----- | ------ |
| 000000 | 10001 | 10010 | 10000 | 00000 | 100000 |
## I-type

| op  | rs  | rt  | imm |
| --- | --- | --- | --- |
| 6   | 5   | 5   | 16  |
- op - the **opcode**, solely determines the instruction
- rs and rt - the **register operands**
- imm - the 16 bit **immediate value** written in two's complement

For example, "addi $s0, $s1, 5" translates to:

| op     | rs    | rt    | imm                 |
| ------ | ----- | ----- | ------------------- |
| 001000 | 10001 | 10000 | 0000 0000 0000 0101 |
## J-type

| op  | addr |
| --- | ---- |
| 6   | 26   |
- op - the **opcode**, solely determines the instruction
- addr - the 26-bit **address operand**

The compiler will create a 32-bit address from the 26 bits of addr (find out why in the next section [[Memory Map and Addressing Modes]])

