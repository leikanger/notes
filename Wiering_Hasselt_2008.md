# Ensemble Algorithms in Reinforcement Learning
Marco A. Wiering and Hado van Hasselt

# Bibtex:
@article{wiering2008ensemble,
  title={Ensemble algorithms in reinforcement learning},
  author={Wiering, Marco A and Van Hasselt, Hado},
  journal={IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics)},
  volume={38},
  number={4},
  pages={930--936},
  year={2008},
  publisher={IEEE}
}

# Min lille oppsummering
Hado og MW går gjennom ulike måter å kombinere handlinger på, majority voting,
type demokrati, rank voting, type grand-prix, og Boltzmann
Multiplication/Addition. 
- BM og BA er to metoder som eg har brukt for å *kombinere lag* i Peer learning,
BA for likestilt kombinering (peers), og BM for prioriterings-kombinering. Eg
har benytta inductive reasoning og mekanistiske modeller for å komme fram til 
dette, noko som kan gjøre resultata interessant å presentere.

Virker som dei kommer fram til at å bruke ensemble av ulike RL algoritmer er
  vedre enn å bruke ensemble av (mange agenter fra) 1 RL-algoritme. 
  Dette kan brukes til å støtte ideen om at der ikkje er nok kompleksitet ved
  en, og at man får guided exploration ved Boltzmann-multiplikasjon av ulike
  algoritmer.
  
Denne artikkelen er mao. også interessant å sitere når eg skal snakke om
Emulated Improvistaion, i og med at dette er en viktig del av diskusjonen:
Dei bruker mykje tid på å finne ut kvifor ensamble mellom ulike modeller er
bedre enn ensamble fra en RL-algoritme, og konkluderer med noke som kan siteres
når man snakker om _directed exploration_!

# Section-for-section
--------------------------
### III. Ensemble Algorithms in RL
"In contrast to previous research, we combine different RL algorithms that learn
separate value functions *and policies*."
"Since the value functions of for example Actor-Chricic that learns preference
values and Q-learning that learns state-action values are of a different nature,
it is impossible to combine their value functions directly."

".. in our ensemble approaches we combine the different policies derived from
the value functions learned by the RL algorithms."

Dei bruker fulle agenter, dvs. utleder policy (til action) før det kombineres. 

Snakker mykje om exploration. Dette er grunnen til at han bruker Boltzmann
distribution over the preference values, virkar det som.
-> HAN BRUKER BOLTZMANN probability distribution for alle, for å få exploration!

*Majority voting*:      Alle agentane stemmer på sin toppkandidat, og [a] velges
etter alle stemmene er talt.
*Rank voting*:        Man gir alle kandidatane ei rangering, og dette summeres opp
over alle agentane: Dersom alle velger en a på andreplass, og ellers varierer
det veldig, blir denne andreplassen nok valgt..
*Boltzmann multiplication*: Gange sammen preferanser (action selection probabilities)
*Boltzmann addition*: Plusse sammen alle preferanser.

### IV: Experiments
1) RL algoritmer med tabulære representasjoner: Small maze task.
2) Partially observable maze. ANN as function approximators.
3) Dynamic maze with obstacles at different positions. ANN.
4) Dynamic maze with goal that moves.
5) Dynamic maze: both element 3 and 4!
ANN was used for experiments 2-5!

###### IV - A:
Sutton's dyna maze. Går gjennom ulike oppsett.

Experimental set-up: 
  - R for å nå målet er +100
  - R for å bumpe mot vegg er -2
  - R for å skape fremdrift -0.1    (per step)
  - Trial blir fullført når Mål er nådd, eller etter 1000 actions.

Dei går gjennom ulike verdier og resultat for ulike spel. Ikkje så veldig
interessant, syns eg..

###### Discussion
Dei skriv at B-multiplication er knallbra.
Og at Majority Voting er bra (sjølv om Hado fortalte meg anna på RLDM)

Han skriv at ensemble gjør det bedre per experience (sample) men brukar meir
computational time:
"Although this is true, many real-world scenarios such as robotics require the
least number of experiences, since the actions taken in real time require much
more time than the actual calculation done by the learning algorithms."

"Experiments also showed that an ensemble with different RL algorithms often
outperforms an ensemble consisting of the best RL algorithms, even thought some
RL algorithms perform considerably worse. This is due to the fact that ensembles
improve independent algorithms most if the algorithms' predictions are less
correlated."
"If the algorithms want to choose the same action, it is more likely that this
action will be explointed than when algorithms disagree."




Mine kommentater OG TANKER:
-----------------------------------------------------------------------
Rank voting er som en DISKRET VARIANT AV peer learning? Forenkla og fæl.
  -> Dette kan vere eit interessant samanlgning når eg skriver om Peer learning!
  
Han skriver i IV: Experiments  at statisk oppsett er brukt for tabulær, og ANN
er brukt for meir dynamiske utfordringer. Min artikkel kan bruke Peer learning
(med monotonsk aukande vekter og prioriteringsverdi gitt av objekt-of-interest).
- Dette kan vere eit viktig bidrag og sample-effektivt tillegg til
funksjonsapproximatsjon for ulike feature-spaces.

Veldig interessant at Boltzmann addition kom så lavt.
Og at Boltzmann multiplication kom så høgt. 
Dette er verdt å undersøke/diskutere nøyare! 
