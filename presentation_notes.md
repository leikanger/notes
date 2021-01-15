# ============== PRESENTATION NOTES =========================
| ** Slide 1 ** | ** Slide 2: RL ** |   |
|               | **                |   |
|               |                   |   |

## Slide 2: Reinforcement Learning Fundamentals (Tabular RL)
### Slide 2a: Agent env. interface:
    - Learner and decision maker is called the agent.
    - What is interacted with : environment
     
#### Reward hypothesis
    (mention :Reward_hypothesis: )
**The reward hypothesis** states:
  That all of what we mean by goals and purposes can be well thought of as the
  maximization of the expected value of the cumulative sum of a received scalar
  signal (called reward).
  
It's important that we do not embed prior knowledge about a task in the 
reward signal; multiple imfamous examples exist where **reward shaping** 
have caused catastrophic failures.
    
When a behaviour is defined by one policy, a given state has a **value** with regards to the current reward scheme.    

### Slide 2:B down: SAR
Talk about $s$, $a$, $r$:
    - RL-doctrine: Goal-directed behaviour can be reduced to 3 signals passing back and forth
        between an agent and its environment.
        * One signal to represent the basis for the next choice (the states)
        * One signal to represent the choices made by the agent (the actions)
    State: the basis of the next choice. Contains all the information necessary for the next choice.
    :Markov_property:
        * One signal to define the agent's goal                 (the rewards)
    
    Hours could be spent on each of these three signals, but we limit ourselves the defining Markov prop

"In a _Markov_ decision process, the probability given by $p$ completerly
characterize the environment's dynamics."
"That is, the probability of each possible value for $S_t$ and $R_t$ depends
only on the immediately preceding state and action, $S_{t-1}$ and $R_{t-1}$, and
given them, not at all on earlier states and actions."
"The state must include information about all aspects of the past
agent-environment interaction that make a difference for the future. If it does,
then the state is said to have the _Markov property_."

    
## Slide 3: Return and value function
#### Return
- The return is the expected reward from one state following one policy to the end.
    -> episodic tasks: simply to sum all rewards from now to end of ep.
- Continual tasks does not easily divide into episodes. Discount factor $\gamma$.

## Slide 4: Physical Interaction Learning
#### 4A - 
#### 4B - curses of robot learning
- Curse of dimensionality: Training time increases exponentially with number of states.
- Curse of real-world sampling: In real-time, but also expensive and potentially dangerous equipment.
- Curse of under-modelling: Can be sampled from a model instead, but RL is imfamous for finding loopholes in the model: Very difficult to transfer learned behaviour from sim. to real
- Curse of goal spesification: Goal specification is def. through the reward function. 
    * Complex environments makes it difficult to train with sparse rewards 
    * better shaped rewards can help training time, but also form the solution.
    * reward engineering can produce unforseen results.
#### 4C - Kaelbling et al 2020
- Deep RL is a general approach, but for creating specific solutions.
##### Challenges for DRL:
- Sample efficiency: Robot learning happens in real time, with wear-and-tear.
- Generalizable: Should be applicable to many situations and tasks. Not possible with DRL.
- Compositional: Should be represented such that it can be combined with previous knowledge.
- Incremental: Capable of adding new knowledge, expanding SS and AS, or abilities over time.
  
Most current DRL approaches do not have these properties: They can learn surprising new abilities, but generally they require a lot of experience, do not generalize well, and are monolithic during training and execution (i.e., neither incremental nor compositional).

# Slide 5: General Value Functions

