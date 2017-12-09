## Talk: On Bayesian Deep Learning and Deep Bayesian Learning

Abstract: _Probabilistic and Bayesian reasoning is one of the principle theoretical pillars to our understanding of machine learning. Over the last two decades, it has inspired a whole range of successful machine learning methods and influenced the thinking of many researchers in the community. On the other hand, in the last few years the rise of deep learning has completely transformed the field and led to a string of phenomenal, era-defining, successes. In this talk I will explore the interface between these two perspectives on machine learning, and through a number of projects I have been involved in, explore questions like: How can probabilistic thinking help us understand deep learning methods or lead us to interesting new methods? Conversely, how can deep learning technologies help us develop advanced probabilistic methods?_

_Bayesian models, in contrast to deep learning models, are a theory-first approach to understanding learning._
Data-led models capture intricacies.
Theory-led models lead to great advancements
Some benefit to be had forcing data-led models through theories

Nonparametric methods:
* Gaussian processes
* Kernel methods
* Neural nets

_Efforts to formalize these models:_
Graphical models
Probabilistic programmign languages, whoa!
Probabilistic Torch!

_Examples of each:_
Bayesian learning: inference in some proba model
* monte carlo, variational inference, GPs, NPBayes, Graphical models, BayesOpt
Hinton: deep learning as optimization of functinos, parametrized by neural nets
* SGD, dropout, RNNs, Conv nets, neural nets, attention

_Review of BAYESIAN THEORY OF LEARNING_
Ideal learner: wants to learn something about the world, but doens’t know state of the world.
Posits a model: the joint distribution over uknown theta (prior) and likelihood
Prior: assumptiosn that agent makes of world, previous knowledge
Posterior: captures agent’s knowledge of the world after it sees X
Once it has posterior, it can use it to predict future observations, use those to maximize utility.

Strengths:
* gives us perfect learner given unlimited resources
* unifies treatment of uncertainties
* explicit expression of prior knowledge/inductive biases in models
Rigidity issue:
* If our assumptions are wrong, then our learning is wrong (kind of difficult to test this in Bayesian context - you have to step out)
* Not all prior knowledge can be encoded as joint distributions (convnets in natural imagery)
* We have to make tradeoffs between efficiency and accuracy - so people generally assume Bayesian techniques are not scalable.

### A few of this guys favorite ideas related to the cross-pollination of ideas between DL and Bayesian learning:

*Posterior server*. _Bayesian techniques make distributing learning less error-prone, because state of truth is aggregated posterior, not aggregated parameters (which requires each worker has correct up-to-date copy of params to be productive)_

Markov chain monte carlo sampling algorithms - random sample converges to posterior
Variational inference: posits parameters of posterior, tries to optimize these parameters. Like mixed gaussian processes, for example.

Distributed SGD is noisy, because you have to sync to parameter server, and this makes it harder for models to converge stably.
In Bayesian context, we just want distribution. As long as every worker is sampling posterior, it’ll be fine!
So instead of parameter server, you have posterior server. Cool.
MCMC = markov chain monte carlo
Samples don’t converge to single point, they jump around and sample from posterior.

Shoutout: Elastic weight consolidation: approximate posterior with something fancy.
Pause, think about this: Params v functions: Params in NNs often don’t have meaning, might be easier to think about priors/posteriors in the space of functions instead (the network can parameterize them).

Switch: how can DL help Bayesian learning.

*Concrete VAEs*. _VAEs are priors/posteriors; reparameterization trick has only worked for continuous vars but we often want discrete variables (like the number or presence of objects in a scene), so this defines a new reparam trick for discrete vars._
Latent variables describes objects in a scene and their pose; relationship between tehse vars and pixels is complex and nonlinear. Modeled by generative neural net.
Goal: maximize log likelihood of ...
ELBO (Evidence Lower Bound): variational posterior = parameterize by another neural net.

Reparameterziation trick:
Difficult to directly optimize variational posterior, because it appears as distribution under which we are taking parameters of ELBO…?
But it only works for continuous latent variables.
But sometimes we want discrete vars! Like presence/number or objects in scenes, or do control flow in generative model - all of these are discrete.
Does reparam trick work for discrete? Yes! Relax them into “concrete random vars”
Take log probas, add Gumbel distributed noise, take argmax.
* Magic of gumbels makes the distribution exactly right!? Wat.
* Soften argmax to softmax with some param lambda.
* And all this is differntiable! So this is now a reparam trick that lets us learn discrete vars.

*FIVO: Filtered Variational Objectives.*
Importance weighted autoencoders.
Variational lower bound: defines it using a statistics idea called Importance sampling.
* Rewrite expectation in terms of posterior somewhow.
* Using math equalities, we can get tighter lower bound ? that helps learning ?

Interface between Bayesian learning and deep learning is exciting! They benefit from each other.

Open questions:
* Being Bayesian in the space of functions instead of parameters?
* How to deal with uncertainties under model misspecification?
    * Uncertainties in posterior - can’t be sure if they’re calibrated or not?
