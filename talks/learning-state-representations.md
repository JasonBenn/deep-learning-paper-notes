## Learning State Representations

_On the face of it, most real-world world tasks are hopelessly complex from the point of view of reinforcement learning mechanisms. In particular, due to the ”curse of dimensionality”, even the simple task of crossing the street should, in principle, take thousands of trials to learn to master. But we are better than that._

_How does our brain do it? In this talk, I will argue that the hardest part of learning is not assigning values or learning policies, but rather deciding on the boundaries of similarity between experiences, which define the ”states” that we learn about._

_I will show behavioral evidence that humans and animals are constantly engaged in this representation learning process, and suggest that in a not too far future, we may be able to read out these representations from the brain, and therefore find out how the brain has mastered this complex problem._

_I will formalize the problem of learning a state representation in terms of Bayesian inference with infinite capacity models, and suggest that an understanding of the computational problem of representation learning can lead to insights into the machine learning problem of transfer learning, and psychological/neuroscientific questions about the interplay between memory and learning._

Ignoring irrelevant parts of env important, depends on task. 
* Calling a taxi = pay attention to colors of cars.
* Helps automatically generalize.

RL curse of dimensionality = the larger our state space, the more policies we need to learn.

Infer when two similar situations are the same and when they’re different. Jaywalking in DC is not equal to jaywalking in NYC (ticket vs no ticket).

Bayesian inference with an infinite capacity prior.
* Generative model
* Observed effects are caused by latent causes (that you’re in NYC)
* A prolific latent cause causes most observations, likely to cause next one
* # of latent causes is infinite (that’s why it’s called the infinite capacity prior)
* Likelhood: each latent cause produces similar observations

Clever experiment demonstrates that humans learn latent causes and cluster events according to those causes.
Learning happens within a cluster, not across cluster boundaries.
Hypothesis: events of same latent cause stored together in memory.
* Experiment of guessing line segments that are closely or not closely related - clever.

Challenge: learn to solve many tasks with little data. Yael thinks we should transform complex tasks into simple ones.
Orbitofrontal cortex (OFC): implicated in good “life choices”, but you can still do well on classic tests, including classic prefrontal cortex tasks
OFC: maybe it’s for storing partially observable states
We can kinda classify next state by reading fMRIs of OFCs.

Open Q: how is this flexible representation created on the fly?

Whoa - make sure extinction happens in the same “latent cause” cluster - if it’s attributed to a different latent cause cluster then it won’t work.
Rat fear response.
