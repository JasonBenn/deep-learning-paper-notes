## Learning disentangled representations for RL

Models of the world are really important. Typically, they are the expected reward r(s, a) and transition dynamics P(s’|s, a)
Good-quality models can be learned from data, but mostly this has a marginal effect of successful control.

Sometimes model-based RL does as well as value/policy-based RL (value: AlphaGo, policy: robotics). Model-based currently does have a lot of success stories, unfortunately.

What parts of the world do we need to model? Think of Space Invaders. You need to model bullets - they might hit you.
Some parts of observation are under our control!
Some parts aren’t under our control, but are informative for future action.
Some information is just noise.
Problem: many models waste resources on all of these components (like the color of the background - and if you change this thing, it’ll get confused).

2010 paper: building models of entire game vs building models (Markov decision processes) of just local environment.
Another paper: trying to learn action-conditional predictions, to try and learn what is and what is not under the agent’s control. Just uses deep learning - somewhat successful. Suggests there may be other better ways to obtain this representation.

Temporal abstraction AKA multi-step predictions.
Looking at error signals from multiple steps. 
