---  
share: "true"  
---  
# CS 470 Midterm  
  
## CS470 – Introduction to Artificial Intelligence  
  
Midterm “Exam”  
  
```  
Instructions for taking the midterm exam (please read in full before starting):  
```  
```  
This pdf is the midterm exam/assignment. You can work on it for as long as you want through March 3. In so doing,  
you can consult with peers, the textbook, the internet, ChatGPT (beware!), etc., though you cannot consult with the  
instructor (to simulate the “real world.”). TAs are also not expected to provide you with answers.Once you are  
satisfied with your answers, you should take theGrading Your Midtermexam on Learning Suite by yourself without  
consulting peers, the textbooks, the internet, etc. The grading exam is timed – you will have 45 minutes to complete  
it) – and is the mechanism for grading this midterm. It will ask you questions about what you answered in your exam.  
You should complete it by Friday, March 3 at 11:59pm.  
```  
```  
To make sure you do not just lean on others as you take the midterm, I recommend that you follow this three step  
process to evaluate what you know, to learn more, and to even help others to learn:  
```  
Step 1 Take an hour or two to see if you can answer the exam questions by yourself. This will give you an idea of what  
you currently know and to evaluate what you still do not understand very well.  
  
Step 2 Consult with peers, the textbook, the internet, etc. Compare and discuss your answers against these other  
resources to enhance and grow your understanding. From this process, improve and correct your answers. But do NOT just copy answers – use these (perhaps awkward) exam questions to instigate learning.  
  
Step 3 By yourself and without consultation with others, the textbook, or the internet (you should only consult the exam and exam notes that you wrote down as part of steps 1 and 2 above), take the Grading Your Midterm exam on Learning Suite to grade your exam. Each question in that exam will reference a question from this exam (which you will have completed in Steps 1 and 2) in a multiple choice or true/false format. If you have correctly and completely answered all of the questions (and learned about the topics) in steps 1 and 2, this should be really easy. The Grading Your Midterm exam is timed, such that you will have 45 minutes to complete it once you have started it. So, find a quiet place to take the grading exam in which you won’t be disturbed for the full 45 minutes (though I suspect it will not take that long for you to complete if you did Steps 1 and 2 properly).  
  
```  
Your grade on the midterm exam will be the score you get on theGrading Your Midtermexam (step 3), and you  
will only be given one chance to take that grading exam.So be careful as you answer the questions. You do NOT  
need to turn in your answers or notes from steps 1 and 2 above.  
```  
  
## Foundations of Agents  
These questions are supposed to explore the basic underpinnings of agents and the common philosophies that AI  
Designers use to construct them.  
1. According to the most common definition among AI scientists, what does it mean to be rational? (Hint: What is the difference between being rational and being omniscient?)  
	1. Being rational is making the best choice with the provided information, or the choice that will maximize your expected utility.  
	2. Agents should ACT rationally but do not need to THINK rationally  
2. In class, we have repeatedly diagrammed a simplified decision-making processes using five different components. What are these five components? How do they impact each other?  
	1. [States](app://obsidian.md/States)  
	2. [Actions](app://obsidian.md/Actions)  
	3. [Consequences](app://obsidian.md/Consequences)  
	4. [Goals](app://obsidian.md/Goals)  
	5. [Utility](app://obsidian.md/Utility)  
3. What are difference between (simple) reflex agents and goal or utility-based agents?  
	1. Simple reflex agents make decisions based solely on the current percept and predefined rules, without considering past percepts or future consequences.   
	2. Goal or utility-based agents, on the other hand, consider both the current state and long-term goals or utility functions to make decisions that optimize outcomes over time.   
	3. They employ internal representations of the world and may use planning and reasoning algorithms to determine the best course of action.  
4. Is a potential-fields agent a reflex agent or a goal/utility-based agent? Why?  
	1. They are reflex agents, pre-planning, and responding to the environment via pre-planned rules  
	2. Since potential fields are precomputed they are NOT utility based agents  
5. Why might an AI Designer choose to create a reflex agent instead of a utility/goal-based agent (and vice versa)?  
	2. **Choose Reflex Agents If**:  
		1. The environment is fully observable  
		2. The environment is deterministic  
		3. There is little time for deliberation (i.e. we must act quickly/instantaneously)  
		4. No learning or adaptation is required  
	3. **Choose Utility Agent If**:  
		1. More complex environment  
		2. Environment is not fully observable  
		3. Lots of local minima  
		- Good amount of deliberation  
6. What common assumptions does an AI Designer make when creating a reflex agent?  
	1. Fully observable environment  
	2. Deterministic environment  
	3. Single-step decisions  
	4. No learning/adaptation required  
	5. Must act quickly  
  
## Game-Playing Agents (Adversarial Search)  
These questions are supposed to explore basic understanding of constructing a standard game-playing agent using  
adversarial search.  
7. Consider the following zero-sum, turn-taking game in which the first player maxis trying to maximize the score, while second player minis trying to minimize the score. (Note: Red letters next to the nodes in the tree are labels for the the nodes of the true.)  
	1. ![Pasted image 20240226122953.png](./assets/Pasted%20image%2020240226122953.png)  
	2. What is the maximin (minimax) value of the game?  
		1. 3  
	3. Which nodes in the tree are not expanded when using alpha-beta pruning?  
		1. S, O  
8. How does alpha-beta pruning change the maximin/minimax value that will be computed compared to what is computed by the minimax algorithm?  
	1. It does not alter the final value of the game. It only changes how you explore the tree, you are guaranteed to find the best value of the game, so if A wins they will win by the value returned or better  
9. On average, how does alpha-beta pruning impact the Big-Oh of minimax search?  
	1. $O(b^{\frac{d}{2}})$  
10. In adversarial search, what is the primary purpose of a heuristic evaluation function?  
	1. Function that estimates the value (“goodness”) of a state  
		2. Still helps our algorithms make informed decisions  
		3. Boosts computational performance  
		4. Caveat: it’s only an estimate  
			1. Something might look good but not be optimal  
		5. Caveat: there are multiple ways to estimate something  
11. What makes a good heuristic evaluation function? (Hint: We talked about several properties in class – they are in your textbook too)  
	1. Include relevant features  
	2. Weight features by importance  
	3. Incorporate domain knowledge  
	4. Have computational efficiency  
	5. Be accurate (i.e. give a reasonable estimate)  
12. In Reversi, transitions between nodes in the tree is deterministic. Could alpha-beta pruning still work in scenarios in which transitions are non-deterministic? Why or why not?  
	1. No, If the outcome of a move is uncertain, it becomes challenging to accurately assess those bounds, leading to potentially incorrect pruning decisions.  
	2. You could use a similar approach, but it would lack the certianty that alpha-beta pruning has  
13. Reversi is a zero-sum game. Would alpha-beta pruning (with the minimax-search algorithm) be a good idea to use in a general-sum game? Why or why not? (Note: We only briefly talked about this in class – you might have to find some additional stuff to come up with an informed answer.)  
	1. Yes it would be, my only concern would be that you may not have enough computational power to do a full tree search. I likely would add a heuristic function to help narrow the search space  
14. Would alpha-beta pruning (with the minimax search algorithm) be a good algorithm if the opponent plays randomly?  
	1. It would work decently well, however, it assumes the opponent always plays the best move available, so it may not work perfectly. It won't maximize potential score of the whole game as well as other approaches might.  
	2. It will however ensure that you get the best outcome no matter what the opponent chooses at any given step  
15. ~~Tanner Clements won our preliminary Reversi Tournament (congratulations, Tanner!). Tanner’s agent used alpha-beta pruning with a clever heuristic function? Was Tanner’s agent intelligent? Why or why not?~~  
	1.   
## Deriving Beliefs  
These questions are supposed to explore basic understanding of creating Bayesian-based beliefs.  
16. After graduation, you receive a job in a government agency in your home country that investigates your government for corruption. The first week on the job you are task with investigating the potential corruption of a high-ranking government official. If you decide to declare that the government official is corrupt, you will write a whistleblower report publicly calling the official out for corruption. Otherwise, you will publicly state (honestly or dishonestly – hopefully honestly) that you do not believe that the government official is corrupt. You decide to use what you learned in CS470 to reason about whether the government official is corrupt. From prior data, you know that 90% of government officials are corrupt. Your agency has also found a connection between government officials that call their mother frequently and those that do not. Only 10% of  corrupt government officials call their mother weekly, while 50% of non-corrupt government officials call their mother weekly. You investigate the call records of the high-ranking government official. In so doing, you discover that the official calls his/her mother weekly. You must now decide whether to file a whistleblower report (stating the government official is corrupt) or publicly state that the government official is not corrupt.  
	1. List the random variable(s) that you believe is/are relevant to reasoning about the corruption of this high-ranking government official.  
	2. Define the sample space (i.e., what are the potential outcomes?) for each random variable listed in part (a).  
	3. Determine the probability that the high-ranking government official you are investigating is corrupt?  
	4. Should you accuse this particular government official of corruption? Actually, you don’t need to answer this question, as it is for the next unit we will cover. The question is just something a foreshadow boy or girl would ask.  
17. Derive Bayes rule using the product rule (which is $P(a,b) =P(a|b)P(b))$.  
	1. First, $P(a,b) = P(a|b)P(b))$.  
	2. Similarly, $P(a,b) = P(b|a)P(a))$.  
	3. Combined: $P(a|b)P(b)) = P(b|a)P(a))$  
	4. $\therefore P(a|b) = \frac{P(b|a)P(a)}{P(a|b)}$  
18. Consider three salient, life-altering events that a person could potentially experience: (1) Eat more than 100 heads of broccoli before turning 6 years old, (2) Advance past the first elimination round of the CS470 Winter 2023 Reversi tournament, and (3) Become a millionaire before turning 90 years old. We model each of these potential experiences as a boolean random variable:  
	1. A: Eat more than 100 heads of broccoli before turning 6; ΩA={a,¬a}  
	2. R: Advance past the first elimination round of Reversi tournament; ΩR={r,¬r}  
	3. M: Become a millionaire before turning 90; ΩM={m,¬m}  
	4. ![Pasted image 20240226123406.png](./assets/Pasted%20image%2020240226123406.png)  
		1. A person became a millionaire at age 89. What is the probability that they ate more than 100 heads of broccoli before turning 6 years old?  
			1. $P(m,a) = P(m|a)P(a)$  
			2. $P(a) = P(m|r,a) + P(\lnot m| r, a) + P(m| \lnot r,a) + P(\lnot m| \lnot r, a)$  
			3. $P(a) = 0.027 + 0.003 + 0.063 + 0.007$  
			4. $P(a) = 0.1$  
			5. $P(m|a) = 0.027$  
			6. $P(m,a) = 0.027 * 0.1$  
			7. $P(m,a) = 0.0027$  
		2. Are the random variables R and M independent?  
			1. $P(m) = 0.027 + 0.035 + 0.063 + 0.215 = 0.34$  
			2. $P(r) = 0.027 + 0.003 + 0.035 + 0.035 = 0.1$  
			3. $P(m) * P(r) = 0.034$  
			4. No they are not b/c $P(m,r) \ne P(m) * P(r)$  
		3. Are the random variables R and M conditionally independent given that a person ate 100 heads of broccoli before turning 6?  
			1. $P(r,m |a) = \frac{P(r,m,a)}{P(a)}$  
			2. $P(r,m |a) = \frac{0.027}{0.1}$  
			3. $P(r,m | a) = 0.27$  
			4. $P(r|a) * P(m|a)$  
			5. $P(r|a) = 0.027 + 0.003 = 0.03$  
			6. $P(m|a) = 0.027 + 0.063 = 0.03$  
			7. $P(r|a) * P(m|a) = 0.0009$  
			8. No they are not b/c $P(m,r|a) \ne P(m|a) * P(r|a)$  
19. Consider the following Bayes Network which depicts the relationship between four random variables: W (whether or not you win the 470 Reversi Tournament), G (whether or not you graduate from BYU), J (whether or not you get a job soon after you leave BYU), and R (whether or not you eventually get rich). ![Pasted image 20240226123501.png](./assets/Pasted%20image%2020240226123501.png)  
	1. Without any information about any of the random variables other than the probability tables given, compute the probability that R=T (i.e., you become rich).  
	2. Suppose that you win the class Reversi Tournament (i.e., W=T). What is the probability that R=T.  
	3. Are W and R conditionally independent given J?  
20. The Bayes Filter is an algorithm designed to reason about the world given uncertain observations and outcomes. Consider a robot that has the ability to move about a world and to sense its environment with a sonar sensor. Suppose the robot has a map of its world. If such a robot is to determine where it is in the world using the Bayes Filter algorithm, name the two probability models (don’t give math notation, state what the two probability models represent)?  
	1.   
21. Locate and label the two probability models you named in the previous question in the follow snippet of pseudo-code: ![Pasted image 20240226123530.png](./assets/Pasted%20image%2020240226123530.png)  
	1. 