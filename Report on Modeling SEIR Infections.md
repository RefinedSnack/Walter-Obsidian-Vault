---  
share: "true"  
---  
# Report on Modeling SEIR Infections  
  
## Name:  
- Walter DeGering  
  
## Abstract:  
This report examines SEIR infection dynamics through agent-based simulations. We investigate the influence of parameters on infection spread across different network structures. We explore standard and alternative configurations, varying p1c (.44) and mu_i (1.0), to understand their impact. We find that adjusting these values increases the max number of infected individuals, decreases variance across many tests, and increases the initial spread rate.  
  
## Introduction:  
The problem of modeling the behavior of SEIR infections is crucial for understanding the dynamics of infectious diseases and informing public health policies. In this report, we explore how different parameters influence the spread of infections within various network structures.   
  
## Experiment Conditions:  
- We randomly generated countdowns to recovered time and countdowns to infectiousness for each agent to introduce variability similar to a human population.  
- We tested two sets of configurations: standard configurations and alternative configurations with increased p1c (.44) and decreased mu_i (1.0).  
  
## Hypotheses:  
  
| Network      | Hypothesis (Standard)                                                            | Hypothesis (Alternative)                                                          |  
|--------------|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
| Barabasi(410)| Expect Fast initial spread, Levels out quickly                                   | Increasing p1c accelerates initial spread, Levels out more quickly                |  
| Barabasi(100)| Anticipate Slower initial spread, Gradual leveling out                           | Expect Fast initial spread, Levels out quickly with increased p1c                |  
| Complete(100)| Predict Most Rapid initial spread, Quick leveling out                                 | Anticipate Slower initial spread, Swift leveling out with increased p1c            |  
| Lattice(10x10)| Expect Slower initial spread, Gradual leveling out                                | Predict Faster initial spread, Quick leveling out with increased p1c              |  
| Dublin(410)  | Anticipate Intermediate initial spread, Moderate leveling out                    | Predict Increased initial spread, Faster leveling out           |  
  
## Graphs:  
  
| Network | Standard | Alternative |  
| ---- | ---- | ---- |  
| Complete(100) | ![complete_graph(100)_std.png](./cs575/cs575_lab1/imgs/complete_graph(100)_std.png) | ![complete_graph(100)_alt.png](./cs575/cs575_lab1/imgs/complete_graph(100)_alt.png) |  
| Lattice(10,10) | ![lattice(10, 10)_std.png](./cs575/cs575_lab1/imgs/lattice(10,%2010)_std.png) | ![lattice(10, 10)_alt.png](./cs575/cs575_lab1/imgs/lattice(10,%2010)_alt.png) |  
| Barabasi(100) | ![barabasi_albert_graph(100)_std.png](./cs575/cs575_lab1/imgs/barabasi_albert_graph(100)_std.png) | ![barabasi_albert_graph(100)_alt.png](./cs575/cs575_lab1/imgs/barabasi_albert_graph(100)_alt.png) |  
| Barabasi(410) | ![barabasi_albert_graph(410)_std.png](./cs575/cs575_lab1/imgs/barabasi_albert_graph(410)_std.png) | ![barabasi_albert_graph(410)_alt.png](./cs575/cs575_lab1/imgs/barabasi_albert_graph(410)_alt.png) |  
| Dublin(410) | ![infect_dublin(410)_std.png](./cs575/cs575_lab1/imgs/infect_dublin(410)_std.png) | ![infect_dublin(410)_alt.png](./cs575/cs575_lab1/imgs/infect_dublin(410)_alt.png) |  
## Discussion:  
In all cases the Alternate Setting created faster initial spread and had a higher max number of tests.  
Something else to note is that the alternate significant reduced the spread of the min and max numbers for all populations. That spread decrease was much more interesting and I think has to do with the tightening of the mu_i variable.  
  
  
## Future Work:  
In future work, we aim to delve deeper into the impact of individual parameters on infection spread. It would be interesting to have a graph where the p1c is specific to individuals and their relationship to others (where each edge has it's own assigned p1c)  
  
  
### Code:  
### main.py  
```python  
import networkx as nx  
  
from population import Population  
  
from graphAnimation import GraphAnimation  
  
from plotCreator import PlotCreator  
  
from copy import deepcopy  
  
from configs import *  
  
    
  
# Create a GraphAnimation instance  
  
# animation = GraphAnimation(population, frames)  
  
    
  
# Save the animation to a file  
  
# animation.save_animation("animation.gif")  
  
# animation.show_animation()  
  
    
  
def run(initial_graph: nx.Graph, file_name: str, frames: list[int]):  
  
    if not animate:  
  
        run_batch(initial_graph, file_name, frames)  
  
    else:  
  
        animate_run(initial_graph, file_name, frames)  
  
def run_batch(initial_graph: nx.Graph, file_name: str, frames: list[int]):  
  
    print(f"Starting {file_name}")  
  
    final_output = []  
  
    for x in range(100):  
  
        population = Population(verbose=False, graph=initial_graph)  
  
    
  
        output = [deepcopy(population.agent_counts)]  
  
        for time in frames:  
  
            output.append(population.step(time))  
  
        if len(final_output) == 0:  
  
            for x in output:  
  
                y = {  
  
                    State.Infectious: [x[State.Infectious]],  
  
                    State.Exposed: [x[State.Exposed]],  
  
                    State.Susceptible: [x[State.Susceptible]],  
  
                    State.Recovered: [x[State.Recovered]],  
  
                }  
  
                final_output.append(y)  
  
        else:  
  
            for x in range(len(output)):  
  
                final_output[x][State.Infectious].append(output[x][State.Infectious])  
  
                final_output[x][State.Exposed].append(output[x][State.Exposed])  
  
                final_output[x][State.Recovered].append(output[x][State.Recovered])  
  
                final_output[x][State.Susceptible].append(output[x][State.Susceptible])  
  
    
  
    plot_creator = PlotCreator(final_output, file_name)  
  
    plot_creator.create_plot()  
  
    plot_creator.save("imgs/" + file_name + ".png")  
  
    print(f"Done with {file_name}")  
  
    
  
def animate_run(initial_graph: nx.Graph, file_name: str, frames: list[int]):  
  
    population: Population = Population(verbose=False, graph=initial_graph)  
  
    
  
    # output = [deepcopy(population.agent_counts)]  
  
    for time in frames:  
  
        population.step(time)  
  
    graph_animation = GraphAnimation(population.step_changes, population.initial_states, initial_graph)  
  
    graph_animation.show()  
  
    
  
def read_graph_from_file(filename):  
  
    fo = open(filename,'r')  
  
    line = fo.readline() # Read file header  
  
    line = fo.readline() # Number of vertices and edges  
  
    if not line:  
  
        print('error -- illegal format for input')  
  
        return  
  
    v = line.split(" ")  
  
    numVertices = int(v[0])  
  
    G = nx.Graph()  
  
    G.add_nodes_from(range(1,numVertices+1))  
  
    while True:  
  
        line = fo.readline()  
  
        if not line:  
  
            break  
  
        #print("Line{}: {}".format(count,line.strip()))  
  
        v = line.split(" ")  
  
        v1 = int(v[0])  
  
        v2 = int(v[1])  
  
        G.add_edge(v1,v2)  
  
        G.add_edge(v2,v1)  
  
    fo.close()  
  
    return G  
  
    
    
  
if __name__ == "__main__":  
  
    frames = range(1,120)  
  
    for vals in val_list:  
  
        run(nx.complete_graph(100), f"complete_graph(100)_{vals}", frames)  
  
        run(nx.grid_2d_graph(10,10), f"lattice(10, 10)_{vals}", frames)  
  
        run(nx.barabasi_albert_graph(100,3), f"barabasi_albert_graph(100)_{vals}", frames)  
  
        run(nx.barabasi_albert_graph(410,3), f"barabasi_albert_graph(410)_{vals}", frames)  
  
        run(read_graph_from_file('ia-infect-dublin.mtx'), f"infect_dublin(410)_{vals}", frames)  
```  
  
### Configs.py  
```python  
from state import State  
  
    
    
  
POPULATION_PROPORTIONS: dict[State, float] = {  
  
    State.Susceptible: 0.90,  
  
    State.Exposed: 0.05,  
  
    State.Infectious: 0.05,  
  
    State.Recovered: 0.00  
  
}  
  
std = True  
  
if std:  
  
    beta: float = -0.00504  
  
    p1c: float = 0.12  
  
    mu_i: float = 2.25  
  
    sigma_i: float = 0.105  
  
    mu_e: float = 1.0  
  
    sigma_e: float = 1.0  
  
    val_list: list[str] = ["std"]  
  
else:  
  
    beta: float = -0.00504  
  
    p1c: float = 0.44  
  
    mu_i: float = 1.0  
  
    sigma_i: float = 0.105  
  
    mu_e: float = 1.0  
  
    sigma_e: float = 1.0  
  
    val_list: list[str] = ['alt']  
  
    
  
STATE_KEY = 'state'  
  
AGENT_KEY = 'agent'  
  
animate = True  
```  
  
  
### Agent.py  
```python  
from configs import p1c, beta  
  
from state import State  
  
import numpy as np  
  
import random  
  
    
  
class Agent:  
  
    def __init__(self, initial_state: State, days_spent_infectious: int, countdown_to_recovered: int, countdown_to_infectious: int) -> None:  
  
        self.initial_state: State = initial_state  
  
        self.days_spent_infectious: int = days_spent_infectious  
  
        self.countdown_to_recovered: int = countdown_to_recovered  
  
        self.countdown_to_infectious: int = countdown_to_infectious  
  
        self.agent_id: str = ""  
  
    def set_agent_id(self, id: str) -> None:  
  
        self.agent_id = id  
  
    def get_agent_id(self) -> str:  
  
        if self.agent_id == None: return "NO ID ASSIGNED"  
  
        else: return self.agent_id  
  
    def get_sample_uniform(self) -> float:  
  
        return random.uniform(0, 1)  
  
    def step(self, state: State, infectious_neighbors: list['Agent']) -> State:  
  
        if state == State.Susceptible:  
  
            neighbor: 'Agent'  
  
            for neighbor in infectious_neighbors:  
  
                r = self.get_sample_uniform()  
  
                if r < neighbor.infectiousness():  
  
                    return State.Exposed  
  
            return State.Susceptible  
  
        elif state == State.Exposed:  
  
            if self.countdown_to_infectious == 0:  
  
                return State.Infectious  
  
            else:  
  
                self.countdown_to_infectious -= 1  
  
                return State.Exposed  
  
        elif state == State.Infectious:  
  
            if self.countdown_to_recovered == 0:  
  
                return State.Recovered  
  
            else:  
  
                self.countdown_to_recovered -= 1  
  
                self.days_spent_infectious += 1  
  
                return State.Infectious  
  
        elif state == State.Recovered:  
  
            return State.Recovered  
  
    def infectiousness(self) -> float:  
  
        div: float = p1c / (1.0 - p1c)  
  
        exp: float = np.exp(beta * (np.power(self.days_spent_infectious, 3.0) - 1.0))  
  
        mult: float = div * exp  
  
        return mult / (1.0 + mult)  
  
    def to_string(self, state: State) -> str:  
  
        return f"Agent[{self.agent_id}]: state={state.to_string()}, c2i={self.countdown_to_infectious}, days={self.days_spent_infectious}, c2r={self.countdown_to_recovered}"  
```  
  
### population.py  
```python  
from agent import Agent  
  
from state import State  
  
from configs import *  
  
import random  
  
import networkx as nx  
  
from copy import deepcopy  
  
import matplotlib.pyplot as plt  
  
from matplotlib.animation import FuncAnimation  
  
import numpy as np  
  
import math  
  
    
  
class Population():  
  
    def __init__(self, verbose: bool, graph: nx.Graph) -> None:  
  
        self.verbose = verbose  
  
        self.graph: nx.Graph = deepcopy(graph)  
  
        self.step_changes: list[tuple[int,str,State,State]] = []  
  
        self.initial_states: dict[str, State] = {}  
  
        self.setup()  
  
    def setup(self):  
  
        agents: list[Agent] = self.create_agents(self.graph.number_of_nodes())  
  
    
  
        for node in self.graph.nodes():  
  
            agent: Agent = agents[0]  
  
            agents = agents[1:]  
  
            agent.set_agent_id(str(node))  
  
            self.graph.nodes[node][AGENT_KEY] = agent  
  
            self.graph.nodes[node][STATE_KEY] = agent.initial_state  
  
            self.initial_states[agent.agent_id] = agent.initial_state  
  
        for node in self.graph.nodes():  
  
            self.vprint(self.graph.nodes[node][AGENT_KEY].to_string(self.graph.nodes[node][STATE_KEY]))  
  
    def generate_countdown_to_recovered() -> int:  
  
        # Parameters for the lognormal distribution  
  
        # Sample from the lognormal distribution for the infectious stage  
  
        dI = np.random.lognormal(mean=mu_i, sigma=sigma_i)  
  
        # Round dI up to the nearest integer  
  
        countdown_to_recovered = math.ceil(dI)  
  
        return countdown_to_recovered  
  
    
  
    def generate_countdown_to_infectious() -> int:  
  
        # Parameters for the lognormal distribution  
  
        # Sample from the lognormal distribution for the exposed stage  
  
        dE = np.random.lognormal(mean=mu_e, sigma=sigma_e)  
  
        # Round dE up to the nearest integer  
  
        countdown_to_infectious = math.ceil(dE)  
  
        return countdown_to_infectious  
  
    
  
    def create_agents(self, n: int) -> list[Agent]:  
  
        if n < 3:  
  
            raise ValueError("Size n must be at least 3")  
  
        self.agent_counts = {  
  
            State.Exposed: 0,  
  
            State.Infectious: 0,  
  
            State.Recovered: 0,  
  
            State.Susceptible: 0  
  
        }  
  
        num_exposed = max(1, int(n * POPULATION_PROPORTIONS[State.Exposed]))  
  
        num_infectious = max(1, int(n * POPULATION_PROPORTIONS[State.Infectious]))  
  
        num_recovered = max(0, int(n * POPULATION_PROPORTIONS[State.Recovered]))  
  
        num_susceptible = n - num_recovered - num_exposed - num_infectious  
  
        if (n != sum([num_exposed, num_infectious, num_recovered, num_susceptible])):  
  
            print(f"Create Agents Failed, n: {n} num_exposed: {num_exposed}, num_infectious: {num_infectious}, num_recovered: {num_recovered}, num_susceptible: {num_susceptible}")  
  
        agents = []  
  
    
  
        for _ in range(num_susceptible):  
  
            agents.append(Agent(  
  
                State.Susceptible,  
  
                0,  
  
                Population.generate_countdown_to_recovered(),  
  
                Population.generate_countdown_to_infectious()  
  
            ))  
  
            self.agent_counts[State.Susceptible] += 1  
  
    
  
        for _ in range(num_exposed):  
  
            agents.append(Agent(  
  
                State.Exposed,  
  
                0,  
  
                Population.generate_countdown_to_recovered(),  
  
                Population.generate_countdown_to_infectious()  
  
            ))  
  
            self.agent_counts[State.Exposed] += 1  
  
    
  
        for _ in range(num_infectious):  
  
            agents.append(Agent(  
  
                State.Infectious,  
  
                0,  
  
                Population.generate_countdown_to_recovered(),  
  
                Population.generate_countdown_to_infectious()  
  
            ))  
  
            self.agent_counts[State.Infectious] += 1  
  
    
  
        for _ in range(num_recovered):  
  
            agents.append(Agent(  
  
                State.Recovered,  
  
                0,  
  
                Population.generate_countdown_to_recovered(),  
  
                Population.generate_countdown_to_infectious()  
  
            ))  
  
            self.agent_counts[State.Recovered] += 1  
  
        random.shuffle(agents)  
  
        return agents  
  
    
    
  
    def step(self, time: int) -> dict[State, int]:  
  
        new_states: dict[node, State] = {}  
  
    
  
        # Iterate over each node in the graph  
  
        for node in self.graph.nodes():  
  
            # Get the current agent and its state  
  
            current_agent: Agent = self.graph.nodes[node][AGENT_KEY]  
  
            current_state: State = self.graph.nodes[node][STATE_KEY]  
  
            self.agent_counts[current_state] -= 1  
  
            # Get the infectious neighboring agents of the current agent  
  
            neighbors: list[int] = list(self.graph.neighbors(node))  
  
            infectious_neighbors: list[Agent] = [self.graph.nodes[neighbor][AGENT_KEY] for neighbor in neighbors if self.graph.nodes[neighbor]['state'] == State.Infectious]  
  
            new_state: State = current_agent.step(current_state, infectious_neighbors)  
  
            self.agent_counts[new_state] += 1  
  
    
  
            # Store the new state in the map  
  
            new_states[node] = new_state  
  
    
  
        # Update the actual states of all agents  
  
        for node, new_state in new_states.items():  
  
            if self.graph.nodes[node][STATE_KEY] != new_state:  
  
                self.vprint(f"{time}: Agent[{self.graph.nodes[node][AGENT_KEY].get_agent_id()}] {self.graph.nodes[node][STATE_KEY]} -> {new_state}")  
  
                self.step_changes.append((time, self.graph.nodes[node][AGENT_KEY], self.graph.nodes[node][STATE_KEY], new_state))  
  
            self.graph.nodes[node][STATE_KEY] = new_state  
  
        self.vprint(f"S: {self.agent_counts[State.Susceptible]}, E: {self.agent_counts[State.Exposed]}, I: {self.agent_counts[State.Infectious]}, R: {self.agent_counts[State.Recovered]}")  
  
        return deepcopy(self.agent_counts)  
  
    
  
    def vprint(self, string: str) -> None:  
  
        if self.verbose: print(string)  
```  
  
### state.py  
```python  
from enum import Enum  
  
class State(Enum):  
    Susceptible = 0  
    Exposed = 1  
    Infectious = 2  
    Recovered = 3  
      
    def to_string(self) -> str:  
        return str(self)[6:]  
      
    def get_color(self) -> str:  
        color_mapping = {  
            State.Susceptible: '#1f77b4',  # Blue  
            State.Exposed: '#ff7f0e',      # Orange  
            State.Recovered: '#2ca02c',   # Green  
            State.Infectious: '#d62728'     # Red  
        }  
        return color_mapping.get(self, '#000000')  # Default to black if value not found  
  
```