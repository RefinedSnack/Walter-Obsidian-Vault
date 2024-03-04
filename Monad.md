---  
share: "true"  
---  
# Monad  
  
A monad allows for the abstraction of task or computation to provide extra information or procedure to a function.  
  
Abstracts over the notion of sequence  
  
Monads are a design pattern that allows the user to chain operations while the monad manages the intricacies of that combination. Monads are a powerful type of modularization.  
A monad is composed of 3 components  
  
1) A wrapper type constructor    
2) A wrapper function **pure or unit** this is the "return type"  
3) A run function **bind or flatmap or >>=**  
  
  
Some examples of this are the option type which handles the absence of a value.  
  
  
Or the writer monad that allows you to tack on an additional bit of data to a value or keep a log of changed values. (a use case for this is an accumulator through a list as the tacked on value and the base being the list itself.)  
  
We used monads several times in class particularly when we went through the lego type function combinations.  
  
Another application is "future" or "promise" that allows for us to do web programming.  
  
![Monad usage and control flow](./Monad%20usage%20and%20control%20flow.md)  
![Lists as Monads](Lists%20as%20Monads.md)  
[State Monad](./State%20Monad.md)  
  
A monad has