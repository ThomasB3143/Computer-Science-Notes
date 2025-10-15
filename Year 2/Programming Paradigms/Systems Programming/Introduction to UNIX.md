Section: [[Systems Programming (Root)]]

UNIX is the first operating system written in C, featuring a simpler and faster approach to its predecessor MULTICS
# The Shell

The shell is a powerful way to perform work on a computer through a text interface. Through it, you can:

- Run programs
- Control how programs work
- Move between and organise directories
- Perform sequences of commands to create complex instructions

Popular choices include Bash and Powershell.

The UNIX Shell is not one monolithic program, instead comprised of many smaller programs, allowing the user to combine them together to make new functionality through **script files** and **pipes**
# Pipes

Pipes provide means of composing tools together in the shell through inputs and outputs. For example, we can redirect input or output using the following:

- `<` to take input from a file
- `>` to write output to a file
	- `>>` will append to a file
	- If the file does not exist, then it is created
- `|` to take the output 