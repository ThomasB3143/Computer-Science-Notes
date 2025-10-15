Section: [[CT Term 1 Topic 3 (Root)]]
3.2.2 - Efficiently Solvable 

- Or tractable 
    
- Can be solved in polynomial time or better 
    
- In the complexity class of P 
    

3.2.3 - Not Efficiently Solvable But Efficiently Checkable 

- Some decision problems such as TSP cannot be solved in polynomial time or better 
    
- But a solution can be verified as "yes" or "no" in polynomial time 
    
- These are efficiently checkable 
    
- These are in the complexity class NP 
    
- Non-deterministic algorithms 
    
    - Check every possible solution and be accepting if at least one solution provides the desired output 
        
    - Time complexity of the shortest accepting computational thread 
        

3.2.5 - The NP Class 

- Non-deterministic polynomial-time 
    
- Decision problems that are efficiently checkable 
    
- All P problems are NP problems because "efficiently solvable implies efficiently checkable" 
    

3.2.6 Polynomial-Time Reductions and Transformations 

- Consider decision problems X and Y, and an algorithm A that: 
    
    - Takes an instance I of X as input and provides an instance A(I) of Y as output 
        
    - Such that instance I of X is a "yes" if, and only if, the instance A(I) of Y is a yes-instance 
        
- Basically converts decision problem X into decision problem Y 
    
- This is a polynomial-time reduction (or transformation) 
    
- Represented formally as X -> polyY 
    

3.2.7 - The Reductions 

- Use previous example 
    
- Y is a P problem using witness algorithm B 
    
- Consider algorithm y as follows 
    
    - Takes input as instance I of X 
        
    - Computer A(I) using A 
        
    - Use B to decide if A(I) is a "yes" instance of Y 
        
- If I is a "yes" instance of X. By definition of A, A(I) is a "yes" instance of Y and so B and y output "yes" 
    
- If I is a "no" instance of X, A(I) is a "no" instance of Y and B and y output "no" 
    
- So y solves the decision problem X 
    
- A is O(n^k), B is O(n^m) so y is O(n^km) 
    
    - This means that if Y is P then X is P if X -> polyY 
        

3.2.8 - NP-Completeness 

- Now assume Y is NP such that for any problem X in NP, X -> polyY 
    
- This is an NP-complete problem 
    
- And if Y is in P then X is in P, hence P = NP (this is the big problem we can't solve) 
    

3.2.9 - We Actually Found an NP-Complete Problem! 

- Satisfiability Problem (SAT) 
    
- We found out SAT is NP but also NP-Complete 
    
- But we can't prove SAT is P to prove that P = NP!!!