---  
share: "true"  
---  
# Louvain Algorithm  
  
  
An Aggregation approach to calculate [Network Modularity](./Network%20Modularity.md)  
  
Step 1:  
- Each node is assigned to its own community  
Phase 1:  
- find change in Q if i joins the community  
- $N(i) =$ neighbors of *i*  
Original Equation  
$$  
\sum_{ij \in E}[A_{ij} - \frac{k_i k_j}{2m}]\delta(C_iC_j)  
$$  
Phase 2:  
- make meta graph  
Phase 3:  
- Apply phase 1 on the meta graph, add in the degree AND the edge weight  
  
  
This matches study I've done on vote aggregation methods like rank choice voting, are these connected simply because they are both agglomeration techniques or is there something deeper