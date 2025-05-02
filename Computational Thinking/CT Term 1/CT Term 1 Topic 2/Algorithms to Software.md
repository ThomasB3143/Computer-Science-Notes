Section: [[CT Term 1 Topic 2 (Root)]]
2.3.1 - Algorithms and Programming Languages 

Algorithms: 

- Work on an input 
    
- Produce an Output 
    
- Has precisely stated steps 
    
- Applied generally to a variety of inputs 
    
- Implemented as a computer program 
    

2.3.2 - Programming Languages 

- Programing Paradigms 
    
    - Different styles of programming determined by concepts and abstractions used 
        
    - Imperative/procedural: 
        
        - Use instructions to change a program's state (like variables) 
            
    - Declarative: 
        
        - Functional programs are collections of mathematical functions 
            
        - Computation is undertaken by combining functions 
            
        - No notion of state 
            
        - Flow of control determined by function composition 
            
        - Logic programs specify a logical solution 
            
        - Consists of a set of axioms, rules of inference and a goal statement 
            
    - Data-oriented: 
        
        - Work with data through manipulating relations 
            
        - Usually for databases 
            
    - Scripting: 
        
        - Designed to automate frequently used tasks 
            
        - Used to help existing programs interact by treating them as separate entities 
            
    - Assembly: 
        
        - Low-level 
            
        - Provide an interface between machine code and a high level-language 
            
    - Concurrent: 
        
        - Provide means for concurrency by supporting different threads 
            
    - Dataflow: 
        
        - Represented as nodes of data and a flow of data 
            
    - Fourth-Gen: 
        

2.3.4 - Why So Many? 

- Productivity 
    
    - Speeding up the process of software development 
        
- Reliability 
    
    - Ensuring correct programs through exception handling and aliasing 
        
- Security 
    
    - Restricting capabilities to prevent malicious use 
        
- Execution speed 
    
    - Obviously sometimes we just want things to be faster 
        
- Curiosity 
    
    - To find new ways to solve problems 
        

2.3.5 - Syntax and Semantics 

- Syntax  - rules that govern what makes the program legitimately written 
    
- Semantics – rules that govern what a program means 
    
    - Denotational semantics 
        
        - Meaning is given mathematically as a mathematical structure like a function! 
            
        - Denotations of program parts can be assembled to give the program itself 
            
    - Operational semantics 
        
        - Meaning given in terms of steps of computation such as changing state 
            
    - Axiomatic semantics 
        
        - Meaning given in terms of a collection of logical properties such as rules 
            

2.3.6 - Compilation vs Interpretation 

- Compiler 
    
    - Translates the high-level program into machine code all at once 
        
    - Runs faster as the execution of the compiled program requires no translation 
        
    - Also can be optimised for performance 
        
    - Analyses for bugs and run-time errors 
        
- Interpreter 
    
    - Repeatedly translates as needed then executes said translations 
        
    - Tend to use memory better as the entire compiled program needn't be stored at one time 
        
    - Aid development in that it can be executed during development to discover bugs without recompiling the entire program 
        

2.3.7 - Compilation 

- Lexical analyser: 
    
    -  Converts high-level program into syntactic components 
        
- Syntax analyser: 
    
    - Recognises syntactic structure of the token stream and creates a parse tree 
        

- Translation phase: 
    
    - Flattens parse tree into linear sequence of intermediate code 
        
- Code generation phase: 
    
    - Converts intermediate code into assembly then to machine 
        

2.3.8 - Lexical Analysis 

- Typically uses regex 
    

2.3.9 - Syntax Analysis 

- Uses context free grammar to describe the syntax of a programming language 
    
- Phrase-structure grammar represented as a tuple (N, T, s, R) 
    
    - T and N are disjoint sets of terminal and non-terminal symbols 
        
    - s is the start symbol 
        
    - R is a finite set of rules