---  
share: "true"  
---  
# Network Modularity  
  
A generalization of [Network Homophily](./Network%20Homophily.md). When you apply Homophily metrics across all possible communities  
  
Modularity is a measure of the AMOUNT of homophily for a given network and set of classes  
  
  
$$  
Bc = \lambda x  
$$  
What problem is solved?  
What is B?  
- The modularity Matrix  
$$  
\sum_{ij \in E}[A_{ij} - \frac{k_i k_j}{2m}]\delta(C_iC_j)  
$$  
  
Are the values of B all positive?  
Which eigenvalue is the *largest*?  
Which eigenvector is chosen?  
Are all the values of this eigenvector positive?