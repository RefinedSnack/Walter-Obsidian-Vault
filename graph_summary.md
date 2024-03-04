---  
share: "true"  
---  
# graph_summary  
  
| Number of New Nodes (Cycles) | 2 | 4 | 16 | 1024 |  
| ----------------------------- | ------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- |  
| 10 | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle10_initial2_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle10_initial4_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle10_initial16_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle10_initial1024_loglog.png) |  
| 50 | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle50_initial2_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle50_initial4_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle50_initial16_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle50_initial1024_loglog.png) |  
| 100 | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle100_initial2_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle100_initial4_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle100_initial16_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle100_initial1024_loglog.png) |  
| 500 | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle500_initial2_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle500_initial4_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle500_initial16_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle500_initial1024_loglog.png) |  
| 1000 | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle1000_initial2_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle1000_initial4_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle1000_initial16_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle1000_initial1024_loglog.png) |  
| 5000 | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle5000_initial2_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle5000_initial4_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle5000_initial16_loglog.png) | ![Degree loglog Distribution](./cs575/cs575_hw3_graphs/final_tests/gdist_cycle5000_initial1024_loglog.png) |  
  
### Questions  
1. Choose some of the interesting results and plot the histogram of the degree distribution. Using the "log-log" plot technique discussed in class, discuss whether the network is scale free.  
	1. As the number of initial nodes increases the fewer cycles are needed for the graph to look like a line   
2. Discuss where the "log-log" technique breaks, meaning look at the plots and talk about where and part of the plot doesn't look like a straight line in "log-log" space.  
	1. The upper and lower ends tend to be bad, lots of small member, and few large ones  
3. Discuss differences you saw in your implementation of the algorithm and NetworkX's implementation. You might not see any.  
	1. I didn't notice any differences  
4. Describe what you observed from your animation and relate it to the phrase "the rich get richer". Discuss what this means for why some networks evolve to display the scale-free property.  
	1. It looks like the early adopters tend to be more connected to existing nodes. This feels analogous to how the first few folks to adopt something that gets popular tend to benefit the most from a fad or trend.  
