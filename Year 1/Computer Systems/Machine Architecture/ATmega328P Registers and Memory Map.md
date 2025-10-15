Section: [[Machine Architecture (Root)]]

Used by the Arduino UNO, the ATmega328P microcontroller sports:

- Harvard architecture
- 8-bit processor (registers and bus)
- 16-bit words (some instructions are 32)

I'm gonna shorten the ATmega32P to the megAT for the rest of this
# Registers

The megAT has 32 general purpose 8-bit registers, mapped on the SRAM memory. We dub these R0-R31 and R26-R31 are actually treated as three 16-bit registers X, Y and Z. These are used for indirect addressing
## Status Register

This is an 8-bit register (not one of R0-R31) used for storing flags
## Memory

There are two main memory spaces, the **Data** and **Program** memory stored in the SRAM/EEPROM and flash respectively
## Program Memory

Stored in flash, it is divided into the boot loader section and the application program section. The program counter is 14 bits wide thus can address 16K program memory locations
## Data Memory

![[Pasted image 20250329204551.png]]
## EEPROM Memory

1KB of Electrically Erasable Programmable Read-Only Memory is organised as a separate space for storing data
# I/O Ports

I/O pins are grouped into three ports, B (digital), C (analogue) and D (digital)

The direction of each pin of a port (input or output) is controlled by **data direction registers** DDRB, DDRC and DDRD. A set bit means output, a cleared bit means input

"SBI DDRB, 4" will declare pin PB4 as output, "CBI DDRD, 2" will declare pin PD2 as input

For input pins, the second bit declares whether there is an incoming electric signal or not. For output pins, the second bit can be set to send a signal through it