Section: [[Digital Electronics (Root)]]

On a most fundamental scale, a **transistor** is an electrically controlled switch that can be turned ON or OFF via a control terminal. The most common is a MOSFET (Metal Oxide Semiconductor Field Effect Transistor)

Transistors form logic gates, and logic gates can feed into more logic gates 

Two ports d and s are connected depending on the voltage of the third port, g, like so:
![[Pasted image 20250327141702.png]]
# Constructing Logic Gates

### NOT
![[Pasted image 20250327141834.png]]
We can see that, when A is high, P1 is off and N1 is on. This means Y is connected to ground and therefore **low**

When A is low then Y is connected to $V_{DD}$ and therefore **high**
## NAND
![[Pasted image 20250327142337.png]]
We can see that both A and B must be on to turn P1 and P2 off to output **low** at Y
# Voltages

The **low** voltage, connected to ground, is zero volts. Historically, circuits used a five volt supply for the **high** voltage. We label this $V_{DD}$ when unspecified.

Modern chips now use lower $V_{DD}$ to save power.
# Logic Levels

To map a **continuous** voltage to a **discrete** binary output, we need to define **logic levels** like so:
![[Pasted image 20250327143002.png]]
This follows the **static discipline**, a guarantee that if inputs meet valid input thresholds, then outputs meet valid output thresholds without falling into the **forbidden zone**
# Moore's Law

Transistor density will double every 2 years