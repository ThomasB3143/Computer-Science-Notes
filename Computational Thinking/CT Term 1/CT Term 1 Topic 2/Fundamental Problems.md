Section: [[CT Term 1 Topic 2 (Root)]]
2.1.3 - Problems in Computer Science 

- Usually concerning repeated journey towards some goal 
    
- Like finding the shortest path between two points in ANY given graph 
    
- Key to problems: 
    
    - Constructive nature of solutions 
        
    - Repeated application 
        
    - Measuring the difficulty of solving problems 
        

2.1.6 - Abstraction 

- Problems solved in computer science are typically abstractions of real-world problems instead of those real-world problems themselves 
    
- Must be represented within a computer program 
    
- Must mirror reality sufficiently such that a solution is relevant to its real-world equivalent 
    
- Abstraction is about eliminating specificity by ignoring details irrelevant to the problem 
    

2.1.9 - Decision Problems 

- Consists of: 
    
    - A set of instances 
        
        - Each having an answer of "yes" or "no" 
            
    - Can use set notation for this 
        
- A decision problem seeks to decide if any given instance is a "yes" or a "no" 
    

2.1.12 - Abstracting Map-Coloring 

- Represent the problem as an undirected and unweighted graph 
    
- Each divided region on the map is represented as a vertex 
    
- Each shared border is represented as an edge between the vertices corresponding to the regions 
    

2.1.15 - Search Problems 

- Either there are numerous acceptable solutions and one is returned 
    
- Or there are no acceptable solutions, which should be signalled 
    
- Consists of: 
    
    - A set of instances 
        
    - A set of solutions 
        
    - For any given instance, we need to find an acceptable solution to that instance 
        
    - Or indicate that there are no acceptable solutions to that given instance 
        

2.1.16 - Decision vs Search 

- Some decision problems correspond to a search problem 
    
- ALL search problems correspond to a decision problem 
    
    - A search problem will either find a solution or state that there are none 
        
    - This corresponds to a binary outcome of "yes" or "no" for a given instance that can be represented as a decision problem 
        

2.1.19 - Optimization Problems 

- Consists of: 
    
    - A set of instances 
        
    - A set of potential solutions for each instance 
        
    - Each solution has a measure of quality or lack of 
        
    - Aim is to return the maximum or minimum quality (or lack of) solution for a given instance 
        
- Need to signal for: 
    
    - Cases where there are no feasible solutions for a given instance 
        
    - Or (for a maximization problem) there are feasible solutions of increasingly large measure