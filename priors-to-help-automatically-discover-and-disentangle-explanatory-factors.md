## Priors to help automatically discover and disentangle explanatory factors (Yoshua Bengio)

### Motivation
Goal is to learn representations that separate different explanatory factors; each of these should explain 1 factor of variation.
Should think outside of the standard IID framework. 
Humans are much better at generalizing, even if unfamiliar distributions - we can even plan for things we’ve never seen before.
Modeling/ML all becomes simpler with the right abstract space.

Problem with unsupervised: nobody tells us what we should be invariant to.
Example: observing speech, separate phonemes from speaker ID.

What is a good representation? There might not be a good formula for every task.
But maybe we can constrain them to be consistent with some aspects of the world - these can be our priors.
For example, preserving maximum information when …

### Clues to disentangling representations
Ways to disentangle (these are all clues AKA priors):
* Most powerful underlying factor (currently): marginal indepedence (can factorize join distribution into one probability function for each variable).
* Consciousness prior
* Causal/mechanism independence - factors that are controllable.

"Latent variables and abstract representatinos to disentangle manifolds"
Creating a mapping between a low level of abstraction and a high level of abstraction, interesting.

### Acting to guide representation learning
"Things that I can change independently of other things (moving an object around in space) are good candidates for high-level features."
Can only be discovered by acting in the world.
Is causal, but agent-specific and subjective.
“Independently Controllable Factors”: add an extra term to training objective: goal is to make a number, “Selectivity”, change a lot when we apply a corresponding policy, compared to change incurred by other factors.
Tasks:
* Predicting the effect of actions
* Predicting the cause of two post-action examples
This is WIP - it’s hard to optimize these things.

### What’s wrong with our unsupervised training objectives?
Ideally, relationships in abstract space should be simple.
Yoshua really likes when training objectives are mostly defined in abstract space.
Log likelihood is trying to account for all of the bits in the data - but most of those are low-level details that just don’t matter that much.
Humans really care about sequences of words.
Unsupervised learning would ideally learn these high-level features instead of us telling them.

### The Consciousness Prior
A new form of representation, inspired by cognition.
High- and low-dimensional abstract space
Conscious prediction over attended variables (soft attention). 

If goal is to predict future, then attention might focus on trivial things to predict.
To improve, we need to pick better training objectives. Ideas:
* Representation learning without reconstruction: maximize entropy of the code (captures lots of information).
* Objective function completely in abstract space

? If neurons reinforce each other (Hopfield-like): they might form a more stable attractor.

Factors don’t make instant-by-instant predictions and plans - often we make plans for a much longer future, and we unroll them over time. Instead of just predicting t+1.
Predicted event would be stored in memory by both name and value - interesting.

Conscious thoughts are a good level of a representation for memorization and memories, whoa.


















