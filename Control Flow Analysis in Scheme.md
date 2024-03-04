---  
share: "true"  
---  
# Control Flow Analysis in Scheme  
**[Paper Link](https://www.ccs.neu.edu/home/shivers/papers/pldi88.pdf)**  
Terms:  
- [Flow Analysis](./Flow%20Analysis.md)  
- [Control Flow Analysis](./Control%20Flow%20Analysis.md)  
  
## Question: Which of these terms are important?  
Some things flow analysis can solve:   
- global constant sub-expression elimination  
- loop invariant detection  
- redundant assignment detection  
- dead code elimination  
- constant propagation  
- range analysis  
- code hoisting  
- induction variable elimination  
- copy propagation  
- live variable analysis  
- loop unrolling  
- loop jamming  
  
## Question:  
"Type information is nonetheless extremely important to the efficient execution of Lisp programs, both to remove run time safety checks of function arguments, and to open code functions that operate on a variety of argument types. Thus **flow analysis offers a tempting opportunity to perform type inference from the occurrence of calls to type predicates in Lisp programs.**"  
  
Why is it tempting to use flow analysis above other options, how does the interaction of having a weak typing system and back propagation naturally lend itself to [CFA](./CFA.md)?  
  
Functions as first class citizens creates the problem in the first place. Binding vs assignments leads you to write your programs differently.   
  
## Question:  
How is [CFA](./CFA.md) different from other program analysis techniques. What are the pros and cons, and where can I learn more?  
  
$\lambda \rightarrow N$  
  
  
  
  
- Why would you want to data-trace a c program  
find range of int maybe 4-18 or something  
  
- Null pointer dref.  
  
- For any program input space: True or False  
  
  
