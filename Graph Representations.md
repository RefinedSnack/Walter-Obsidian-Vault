---  
share: "true"  
---  
  
# Graph Representations  
  
If there is a 1 there is an edge, 0 is no edge  
  
### Adjacency matrix  
![Pasted image 20240111140726.png](./assets/Pasted%20image%2020240111140726.png)  
- Helps to identify important nodes  
- Helps to find communities  
- Shows up on random network surfing  
  
### Adjacency List  
![Pasted image 20240111141233.png](./assets/Pasted%20image%2020240111141233.png)  
  
  
### List vs Matrix Representations  
Choose Adj. List for sparse graphs, Adj. Matrix for dense graphs  
Adj. List has slower lookups order n  
Adj. Matrix has fast lookups  
Adj. List takes up less space (in sparse matrixes)  
  
  
![Incidence Matrix](./Incidence%20Matrix.md)  
  
#### Bipartite Graph version  
![Pasted image 20240111142416.png](./assets/Pasted%20image%2020240111142416.png)  
  
1. Break into 2 parts  
2. Show part 1 as columns, part 2 as rows  
3. This is Powerful but struggles with directed edges  
![Graph Laplacian Matrix](./Graph%20Laplacian%20Matrix.md)  
![Oriented Incidence Matrix](./Oriented%20Incidence%20Matrix.md)  
  
  
| Term | Meaning |  
| ---- | ---- |  
| Vertex set: V | Set of items of interest in network |  
| Edge set: E | Relationship between items |  
| Graph: | Network representation |  
| Adjacency matrix: A | Mapping (e.g., dictionary) of who is adjacent from whom |  
| Adjacency list | Matrix of who is adjacent to whom |  
| Incidence matrix: B | Matrix of which edges are incident to whom |  
| Graph Laplacian: L | Diagonal matrix - adjacency matrix |  
  
