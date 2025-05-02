Section: [[Machine Architecture (Root)]]

To program in AVR assembly, we create a C++ shell file and a separate linked file for the assembly code. The "setup()" function defines the program's inputs and outputs whereas the "loop()" function repeats continuously, which is often desired for an embedded system
## Directives

The assembly code contains some statements called **directives**. They don't link to instructions, but are used for things such as defining constants for easier development of assembly code. These are often precented by a dot

The "equ" directive assigns a constant to a label so it can be used throughout the program