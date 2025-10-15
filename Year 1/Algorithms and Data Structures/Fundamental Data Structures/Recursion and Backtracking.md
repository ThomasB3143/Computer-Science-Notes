Section: [[Fundamental Data Structures (root)]]

A **recursive algorithm** is one that calls itself in the **general case**, and does not in the **base case**. The algorithm must change its state and move **towards** the base case
## Memoisation

Some recursive algorithms will lead to multiple calls with the **same arguments**. In this case, we can store the result of these intermediate function calls, as their results will not change over time. The act of storing the result of a computation to retrieve it again alter is called **memoisation**

[[Hash Tables]] are a good place to implement this 
## Backtracking

When we are given many **candidate** solutions, we can build up the solution one step at a time and **backtrack** when we are unable to continue. It works something like this:

1. Do we have a solution?
2. If yes, then return it!
3. If no, then extend in all possible forms until a solution is returned
4. If we have extended in all ways and not received a solution, then give up
![[Pasted image 20250410150800.png]]
