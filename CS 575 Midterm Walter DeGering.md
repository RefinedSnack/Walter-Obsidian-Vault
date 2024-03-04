---  
share: "true"  
---  
# CS 575 Midterm Walter DeGering  
  
## Part 1 - Model Discussion  
  
### Ideal Properties  
They propose the ideal properties of a general model (numbered):  
1. Low density  
2. A max limit on the degree of any node  
3. Differences in the size of each individuals personal network  
4. A fat-tailed distribution (sometimes)  
5. Assortativity by degree of connectivity  
6. High Clustering  
7. Community Structures (highly connected within themselves)  
8. Short path lengths (small world effect)  
9. Generality (does not depend on any one specific quirk of any specific social network not shared with others)  
  
#### 1. Low Density  
Low density makes sense here. Individuals are generally limited in their max number of connections. Provided this effect is strong enough and the population large enough, it would naturally produce sparse networks.  
  
#### 2. Max Limit on Degree  
Hamil and Gilbert argue that the number of close confidants for any person will average about 2 or 3. They lean on previous work to make this argument and I see no issue. However many networks that they want to model are based on an "acquaintance" model or an even more vague "I follow you on Twitter" relationship. While a person is limited in how many close friends they can have, many will elect the follow or be followed by many others in these more vague relationships. As such this does not meet their 9th criteria of being General.  
  
#### 3. Differences in the size of each individuals personal network  
This point is consistent with their cited sources. It also helps to balance the previous rule being not ideal for all kinds of nodes. I would think 2 and 3 should be combined into a single general policy.  
  
#### 4. A fat-tailed distribution  
This point is the only listed optional parameter. I do not know if this is necessary as an ideal if it does not apply to all or most networks.   
  
#### 5. Assortativity by degree of connectivity  
This point is well justified. When applied to known social networks Assortativity is positive.   
  
#### 6. High Clustering  
Social networks are usually homophilic networks. This means that people tend to link with those who are similar to them, be it demographic, social, or physical closeness.   
  
  
#### 7. Communities  
This particular property is difficult to judge as one must identify communities first to measure homophily. So this should be expanded slightly to "easy and clearly observable communities"  
  
#### 8. Short Path Lengths (Small world)  
This feels reasonable and is reflected in real world networks. I don't know if this was well justified here, perhaps in it is in the works cited. However, it is a gap that I am comfortable with. This particular property seems desirable in representing social groups even if it is not totally general.  
  
#### 9. Generality  
This particular point is good, but more of a philosophical one. They are setting out to make a general model, so that is the standard by which they should be judged. Their network then must fit their proposed use case of "most" social networks, and leave out more general criteria.  
  
### Model Parameters  
The proposed model is an agent based model. This will mean that several "rules" will hold determining how, when, and where edges are added.  
  
#### Social Reach  
The model is tuned to allow different kinds of reach. A smaller circumference indicates smaller reach and more intimate relationships. A larger circumference means more  reach and less intimate relationships. For example the difference between a close friend and an acquaintance.  
#### Reciprocity  
 `Agents are only permitted to link with agents who can recipricate`  
 ![Pasted image 20240223122206.png](./assets/Pasted%20image%2020240223122206.png)  
Both agents must be able to" know each other". So if the reach of one is too small the agents do NOT have reciprocity and cannot connect  
  
#### Population Size and Density  
Simulations involving 1,000 agents across a grid of nearly 100,000 cells, density was about 1%.  
The paper gives no justification for this size. It seems reasonable to use this as it is an achievable simulation.  
  
  
#### Clustering  
Clustering is a property this method gets for free. Since agents with similar reach in similar locations will naturally connect to most of the same communities.  
  
#### Two Reaches  
The model through this point does not give a fat-tailed distribution. The necessity of this property is questionable but you can extend this model with the Two Reaches to obtain this.   
  
Using this the "blue" nodes turn into Bridgers, connecting between communities.  
  
This must be balanced but tuning the size of the blues reach, the number of "blues". Adding this property weakens the assortativity.  
  
This property does generalize to any number of reaches, with the expected tradeoff.  
  
## Part 2 - Simple Contagions  
  
### One Reach Variation  
Simple Contagions would spread well and quickly within the community of an infected person. The groups are very clustered and it would do well. However, it will struggle to cross from one community to another.  
  
### Two Reach Variation  
Simple Contagions would spread quickly within a community. Not quite as well and the One Reach but still more than enough. Beyond that, it would have a much easier time crossing with the "blue" nodes acting as community bridges.  
  
### N-Reach Variation  
As the number of reaches goes up it's ability to spread within the community will decrease, and the ability to cross communities will increase.  
  
### In General  
Overall, this network seems ideal for spreading simple contagions. It creates closely connected clusters and then adds bridges between those communities.   
  
## Part 3 - Complex Contagions  
  
### One Reach Variation  
Complex Contagions would spread well and quickly within the community of an infected person provided a critical mass of people are infected within that group. Getting to that point will be difficult, as this setup will have a nearly impossible time crossing communities. The clusters on this network would each then need to go through this.  
  
### Two Reach Variation  
This is the same as the One Reach Variation, however, the difficulty of exposing the communities is slightly eased. This means that instead of each community needing to go through the same difficult infection period that one enough clusters are completely infected the contagion will cascade across all of them.  
  
### N-Reach Variation  
The critical mass of infected communities becomes a smaller number as N increases. However, since more members of each community will have outgroup connections it will be very difficult to infect an entire community.  
  
### In General  
Overall, this network seems to be very well established to protect against complex contagions, there likely exists a value of N that will maximize the spread of a complex contagion. If I had to guess it would be 2 or 3.  
