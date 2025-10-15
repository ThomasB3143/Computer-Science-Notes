Section: [[Digital Electronics (Root)]]

Karnaugh Maps provide a graphical way of representing truth tables to form a simplified equation
![[Pasted image 20250327151509.png]]
In this example, we can see that  $\overline A\;\overline B\;\overline C$ and $\overline A\;\overline B\;C$ can be simplified to just $\overline A\;\overline B$

The process is to circle exactly all ones in the map using as few rectangles as possible and making each rectangle as large as possible. Keep in mind that each rectangle must have its height and width equal to a power of 2.

Each rectangle will represent an implicant, the implicant will be the product of all variables in the rectangle that **don't** change

You can even have your rectangles wrap around like pacman!
![[Pasted image 20250327154745.png]]
Sometimes you will have an unspecified output that is irrelevant, this can be assumed as a 1 or 0 for the sake of maximising your rectangle
# PoS through Karnaugh

Instead of SoP, we can circle the zeros in a map and each circle will represent an implicant using the **negation** of each variable that does not change. Here is a nifty example:
![[Pasted image 20250327155349.png]]
