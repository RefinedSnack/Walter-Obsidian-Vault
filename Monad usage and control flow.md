---  
share: "true"  
---  
# Monad usage and control flow  
Begin with unwrapped thing  
  
call the wrapper function  
  
then run  
then unwrap  
  
The monad does all of this in one step but knowing how the steps work can be powerful.  
  
A call to a monad can look like  
  
~~~c++  
wrapperfunction(thingYouWrap, runFunction)  
~~~