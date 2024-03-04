---  
share: "true"  
---  
# Girvan Newman Modularity  
  
```  
1. Greedily delete high betweenness edges using Girvan Newman Betweenness  
2. Check if you have 2 or more distinct communities  
   2A. If yes: compute modularity and record it  
	   2Aa. label classes  
	   2Ab. restore all edges  
	   2Ac. compute modularity  
	   2Ad. record modularity and class labels  
   2B. If no: return to step 1  
3. Repeat until all edges are deleted (or until it's not worth your time any more)  
4. Select the partition that maximizes modularity on the graph  
```