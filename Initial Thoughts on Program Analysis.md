---  
share: "true"  
---  
# Initial Thoughts on Program Analysis  
  
Look for the beginning  
  
Try to understand 2 things about every variable and function. Their type and their purpose. Type is usually fairly easy to get when in the contexts I use most often where the languages have fairly expressive and well enforced type systems. What is more difficult is understanding the purpose of something. For example a variable named `counter` is obviously used to track the count of something. What specifically is it counting? by what increment.   
  
To answer questions like that I would look at use. When updated what is used to determine when it is changed? What conditions occur.   
  
Here my systematic approach is to look at type first and then to ascertain purpose based on the context of how it is used and what things are named.  
  
Look for [Invariant](Invariant.md)s.  
  
Approaches, run some tests either by hand or automatically to verify the thing I am trying to reason about.  
  
I may try to make an argument along the lines of this function is called in only 2 places and the only possible uses pass in strings that fit the expected format so this function is used in this way.  
  
Making arguments like that for complicated things is very difficult. 