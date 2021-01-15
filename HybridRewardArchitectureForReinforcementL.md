# Hybrid Reward Architecture for Reinforcement Learning
@inproceedings{van2017hybrid,
  title={Hybrid reward architecture for reinforcement learning},
  author={Van Seijen, Harm and Fatemi, Mehdi and Romoff, Joshua and Laroche, Romain and Barnes, Tavian and Tsang, Jeffrey},
  booktitle={Advances in Neural Information Processing Systems},
  pages={5392--5402},
  year={2017}
}

# Abstract
One of the main challengers in RL is generalization. In typical DRL methods this is achieved by approximating the opt. value func. with a low-dimentional repr. using deep network. .... Learning can be slow and unstable. This paper .. new method, called Hybrid Reward Architecture (HRA). 
HRA takes as input a decomposed reward function and learns a separate value function for each component reward function.
Because each component typically only depends on a subset of all features, the corresponding value function can be approximated more easily by a low-dimentional representation, enabling more effective learning. 
....

# Mi korte oppsummering
Arjun anbefalte meg å lese denne artikkelen etter at eg forklarte samme ideen, som eg hadde når eg var å jogga trail i Frankrike.

Dei kjører masse agentar, en for kvart element i brettet for PacMan, frukter, det-som-må-samles, og monster, og handlinga som blir tatt er bestemt som eit aggregat av desse. Trur dei nyttar gjennomsnitt for å velge action.

## Introduction
Kort og kompakt gjennomgang av en bakgrunnsstoff. Review section for dei siste åra (siden 2015) som går gjennom nye moglegheitar Deep Learning innfører for RL.

"Simular to the Horde architecture (Sutton et al., 2011), all these agents can learn in parallel on the same sample sequence by using off-policy learning."
"Each agent gives its action-values of the current state to an aggregator, which combines them into a single value for each action. The current action is selected based on these aggregated values."

## Related Work
Our work builds on upon the Horde architecture: "The horde architecture consistes of a large number of 'deamons' that learn in parallel via off-policy learning." Trains its own general value function (GVF) based on its own policy and pseudo-reward function.
"A pseudo reward function can be any feature-based signal that encodes useful information."

"UVFA (Schaul et al., 2015) builds on Horde as well, ... UVFA enables generalization across different tasks/goals. It does not address how to solve a single, complex task, which is the focus of HRA."

"There are als osimilarities between HRA and UNREAL (Jaderberg et al., 2017). Notably, both solve multiple smaller problems in order to tackle one hard problem. However, the two architectures are different in their workings, as well as the type of challenge they address."
"UNREAL is a technique that boosts representation learning in difficult scenarios. It does so by using auziliary tasks to help train the lower-level layers of a deep neural networkd."
...
"By contrast the architecture breaks down a task into smaller pieces. HRA's multiple smaller tasks are not unsupervised; thay are tasks that are directly relevant to the main task." => DET VIRKER SOM OM DETTE MÅ GJØRES MANUELLT?

"Options are temporally-extended actions that, like HRA's heads, can be trained in parallel based on their own (intrinsic) reward functions."
"However, once an action has been trained, the role of its intrinsic reward function is over. A higher-level agent that uses an opteion sees it as just another action and evaluates it using its own reward function. ... does not make the higher-level agent less complex."

"The heads of HRA represent values, trained with components of the environment reward. Even after training, these values stay relevant, because the aggregator uses them to select its action."

## 3 Model
[God, kompakt, gjennomgang av MDP modellen]
### 3.1 Hybric Reward Architecture
DQN : Estimate Q\* by minimizing the sequence loss function ...
"That the training target is consistent says nothing about how easy it is to learn that target. For example, if R_env is sparse, the default learning objective can be very hard to learn. In this case, adding a potential-based additional reward signal to R_env can yield an alternative consistent learning objective that is easier to learn."
"We propose to decompose the reward function R_env into n reward functions: [eq] and to train a separate RL agent on each of these reward functions."
"..., the decomposition should be such that each reward function is mainly affected by only a small number of state variables."

"Action selection for HRA is based on the sum of the agent's Q-value functions, which we call Q_HRA."

"Acting greedily with respect to the Q-values of a random policy meight appear to yield a policy that is just slightly better than random, but, surprisingly, we found that for many navigation-based domains Q_hra acts as a semi-consistent traning target."

### 3.2 Improving Performance further by using high-level domain knowledge.

## 4 Experiments
### 4.1 Fruit Collection Task
### 4.2 ATARI game: Ms. Pac-Man
Pac-Man har 4 forskjellige kart: "(Separate GVFs are learnt for each of the four maps)."
"By wandering around the maze, it discovers new map locations it can reach, resulting in new GVFs being created. Whenever the agent finds a pellet at a new location it creates a new head corresponding to the pellet."

"The Q-values for an object (pellet/fruit/ghost/blue ghost) are set to the pseudo Q-values of the GVF corresponding with the object's location (i.e. moving objects use a different GVF each time), multiplied with the weight that is set equal to the reward received when the object is eaten."
KORLEIS FÅR MAN TIL Å LAGE VERDI FOR ALLE POSISJONANE NÅR ghost BEVEGAR SEG RUNDT, DA?

"For exploration, we test two complementary types of exploration. Each type adds an extra exploration head to the architecture."
...
"The second, which we call count-based, adds a bonus for state-action pairs that have not been explored a lot."     -  Full detail in appendix..

## 5 Discussion
"One of the strengths of HRA is that is can exploit domain knowledge to a much greater extent than single-head methods."

"HRA solves MS. Pac-Man by learning close to 1,800 general value functions."
"This results in an exponential breakdown of the problem size: whereas the input stat-espace corresponding with the binary channels is in the order of 10^77, each GVF has a state-space in the order of 10^3 states, small enought to be represented without any function approximation. While we could have used a deep network for representing each GVF, using a deep network for such small problems hurt more than it helps, as evidenced by the experiments on the fruit collection domain."



# MINE KOMMENTARAR:
Dei nyttar samme R-scalar når man setter reward for å få frukter (som er positiv reward med størrelse lik poenga man får) og når man dør, som setters til minus 1000. Dette meinar eg er unødvendig, siden dei uansett blir lagt inn ved superposisjon, og man kan godt ha negativ reward på -1 når man mistar eit liv. Dette domenet er også eit godt grunnlag for å lage Reward-vectors, som kan gi ytterligare kontroll over prioriteringa for agenten!
Dei forsøker også å gjøre noko som god kunne vore resultatet av dette over, men uten å gjøre det eksplisitt. Dei summerar over alle event som lagar poeng, så skalerar dei og legg til Q-verdian til ghost (det som fører til tap av liv) separat.
