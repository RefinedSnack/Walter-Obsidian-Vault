---  
share: "true"  
---  
# Diagram Threat Modeling  
  
![Pasted image 20240112121405.png](./assets/Pasted%20image%2020240112121405.png)  
  
![Pasted image 20240112121417.png](./assets/Pasted%20image%2020240112121417.png)  
  
Ask: “Where can bad things happen? How?”   
  
Add more structure and focus to this process by turning the architectural diagram into an informal data flow diagram: trace the flow of data through the system for a simple task, transaction, or service.   
  
Examining this, again ask: “What could go wrong?” Then consider more complex tasks, and eventually all representative tasks.   
  
Consider user workflow: trace through user actions from the time a task begins until it ends. Begin with common tasks.   
  
  
Move to less frequent tasks, e.g., account creation or registration (de-registration), installing, configuring and upgrading software (also abandoning, uninstalling).   
  
Consider full lifecycles of data, software, accounts (Figure 1.7).  
  
Related to [Threat Modeling](./Threat%20Modeling.md)  
  
| Aspect | Informal Data Flow Diagram                  | User Workflow Diagram                        |  
|-------------------------------|--------------------------------------------------|---------------------------------------------------|  
| **Focus**                     | Visualizes data flow within the system.          | Illustrates step-by-step user actions.             |  
| **Elements**                  | Processes, data stores, data flow, external entities. | Activities, decision points, user interactions.  |  
| **Purpose**                   | Identifies data movement and potential issues.   | Explores user experience in task execution.       |  
| **Example**                   | Mapping data flow for order processing.          | Tracing user actions for account creation, software installation, etc. |  
| **Analysis Approach**         | Start with simple tasks, progress to complex ones. | Begin with common tasks, move to less frequent ones. |  
| **Risk Assessment**           | Ask "What could go wrong?" during analysis.      | Consider potential issues in user interactions.  |  
| **Full Lifecycles**           | Explore data, software, and account lifecycles.  | Consider full lifecycles for comprehensive understanding. |  
