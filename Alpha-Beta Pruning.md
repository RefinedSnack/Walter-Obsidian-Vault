---  
share: "true"  
---  
# Alpha-Beta Pruning  
  
- Used with [Minimax](./Minimax.md)  
- Goal is to Decrease the number of nodes needed to evaluate  
- Not an estimation   
	- Gives you a speedup without sacrificing accuracy  
- Prunes branches that do not work on the final tree  
  
- Assigns alpha to player 1, beta to player 2  
	- Alpha is best player 1 (Max)  
	- Beta is best player 2 (Mini)  
  
Steps:  
1. Push Alpha and Beta down to children  
2. Update beta to the smallest alpha of its children  
	1. Unless its terminal  
3. Update alpha to largest alpha of its children  
	1. Unless it's terminal