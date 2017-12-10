## Generative Adversarial Imitation Learning

tl;dr: think of imitation learning as a generative learning problem. It’s much harder than training a GAN because it involves RL.
Next phase: towards unsupervised learning of latent structure from demonstrations.

### Overview
For RL agent to do well in environments, we need to capture high-level features from high-dimensional raw observations.
RL needs cost/reward signal. This is easy for videogames… but can be much harder to write these down in e.g., self-driving situations.
Thus, it’s sometimes easier to take the ML approach of showing them data and having the agent learn from it.

### Approaches to imitation learning
Simplest approach: behavior cloning. Supervised. 
Problems:
* Small errors compound over time. Kind of like covariate shift (distribution shift from training time)
* Can gloss over the fact that human decisions are purposeful and incorporate planning.

Alternative approach: inverse RL. We assume that the human is optimizing for an unknown plan/cost function, and so we guess at it to minimize differences in observations.
Problems:
* Expensive to run RL within a training loop

Alternative: apprenticeship learning. We try to find a policy that ensures that we always pay a cost that’s on par with the expert. 
Costs are kind of like classifications: high costs = non-expert, low costs=things that look like the expert.
SO to minimize, you seek low cost states.

Can think of inverse RL as a kind of generative modeling problem - find the right policy function.
IRL is the daul of an occupancy measure matching problem.

### Using GANs in imitation learning
Solution: use a more expressive class of cost functions. GANs!
Nice thing about GANs: they can handle super high D feature spaces.
Learning from Torcs (examples of driving simulations).

### InfoGAIL
Maximize the mutual information between the latent variables and our observed variation
