Section: [[Digital Electronics (Root)]]
# Combinatorial Circuits

In these circuits, the output only depends on the current input
## Half-Adder

This inputs A and B, and outputs a sum and a carry. This represents binary addition on the values A and B, which can each be either 1 or 0.
![[Pasted image 20250327160334.png]]
## Adder

Provides an additional input, the carry of the previous bit. This then uses two [[Circuits#Half-Adder|half-adders]], one to add A and B, then another to add the carried bit.
![[Pasted image 20250327160525.png]]
We can chain adders to add entire binary strings!
![[Pasted image 20250327160944.png]]
## Subtractor

We can use NOT gates for one string, and add 1 to the start to essentially form the negative of one string. This creates a subtractor like so:
![[Pasted image 20250327161116.png]]
## Decoder

Has $N$ inputs and $2^N$ outputs. It exerts exactly one of its outputs based on the binary number represented by the input bits. We call the outputs "one-hot" because only one is hot (high) at a given time
## Multiplexor (Mux)

Has $k+2^k$ inputs and only one output. The first $k$ inputs represent a binary number. That number is used to select which of the $2^k$ inputs are outputted
## Tristate

A normal buffer has a 1 or 0 at its output, a tristate buffer can be disconnected from the bus wire. When the enable bit is 1, the input is equal to the output. Whereas when the enable bit is 0, the output is floating (this means that no current is output)

We can use a tristate to make a multiplexor, by using the enable bit to select a specific input to be output
![[Pasted image 20250327162820.png]]
## Building our ALU

![[Pasted image 20250327163049.png]]
