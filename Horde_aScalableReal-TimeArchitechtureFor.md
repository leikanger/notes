# Horde: A salable Real-time Architecture for Learning Knowledge from
Unsupervised Sensorimotor Interaction

### Bibtex ?
@inproceedings{sutton2011horde,
  title={Horde: A scalable real-time architecture for learning knowledge from unsupervised sensorimotor interaction},
  author={Sutton, Richard S and Modayil, Joseph and Delp, Michael and Degris, Thomas and Pilarski, Patrick M and White, Adam and Precup, Doina},
  booktitle={The 10th International Conference on Autonomous Agents and Multiagent Systems-Volume 2},
  pages={761--768},
  year={2011},
  organization={International Foundation for Autonomous Agents and Multiagent Systems}
}

## Abstract

## Section 1
"In this paper we pursue a novel approach to knowledge representation based on the notion of value functions and on other ideas and algorithms from reinforcement learning."
"In our approach, knowledge is represented as a large number of approximate value functions learned in parallel, each with its own policy, pseudo-reward function, preudo-termination function, and preudo-terminal reward function."

Skriver også masse referanser om kven som har sett på dette før. Gull!
Sjekk "Ring (1997) explored continual learning of a hierarchical representation of sequences."

## Section 2: Value functions as semantics
"The idea of the present work is that the value-function approach to grounding semantics can be extended beyond reward to a theory of all world knowledge."
GOD GJENNOMGANG AV TEORI. Value functions, RL, policies, etc.

## Section 3: From values to knowledge (General Value Functions)
Veldig bra gjennomgang, og skaper masse ideer å lese det! Gjør det igjen!

"... defined with arbitrary functions r and z action as pseudo-reward function and preudo-terminal-reward function."
For example. ....

Går gjennom dei 4 parametre som inngår i GVF: pi, r, z, gamma
pi  - policy
r   - pseudo reward for ulike states
z   - pseudo terminal reward for pseudo-termination function gamma.

"Formally, we define a general value function, or GVF, as a function q : S x A => R with four auxiliary functional inputs pi, gamma, r, and z, defined over the same domains and ranges as specified earlier, but now taken to be arbitrary and with no necessary relationship to the base problem's reward, terminal-reward, and termination functions: [formel]"
"Note that conventional value functions remain a special case of GVFs."

## Secition 4: The HORDE Architecture
"The Horde architecture consists of an overall agent composed of many sub-agents, called demons. Each demon is a independent reinforcement-learning agent responsible for learning one small piece of knowledge about the base agent's interaction with its environment. Each daemon learns an approzimation, q^, to the GVF, q, that corresponds to the daemon's setting of the four question functions, pi, gamma, ra, and z."

BRUKER RESTEN AV AVSNITT FOR GVF teknikk. Les dersom eg vil gjøre noko meir generellt enn Pret!

"For a typical GVF, the actions taken by the behavior policy will match its target policy only on occasion, and rarely for more than a few steps in a row, For efficient learning, we need to be able to learn from these snippets of relevant experience, and this requires off-policy learning."

Sjekk   GQ(lambda) - Maei & Sutton 2010

"One can think of the demons as being of two kinds. A demon with a given target policy, pi, is called a prediction demon, whereas a demon whose target policy is the greedy policy with respect to its own approximate GVF (i.e. pi = greedy(q^hat) or pi(s, arg max_a q^hat(s,a,phi)) = 1) is called a control demon." 
"Control demons can learn and represent how to achieve goals, whereas the knowledge in prediction demons is better thought of as declarative facts."

## Resten av artikkelen handlar om det spesifikke ekspreimentet. Les dersom interessert!

