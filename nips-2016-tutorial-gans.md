## [NIPS 2016 Tutorial: Generative Adversarial Networks](http://arxiv.org/abs/1701.00160)

_Dec 2016_

tl;dr: this (lengthy) paper is awesome. A perfect introduction to GANs.

### Key points

#### Why generative modeling is a topic worth studying

* Highly dimensional probability distributions are useful, hard to get right, and generative models are a great way to build them and sample them.
* Generative models are useful for RL. It's useful for RL agents to be able to "imagine" the future.
* It's powerful to generate future time series data (stock market predictions, etc).
* Generative models can realistically fill in missing data for semi-supervised learning.
* A whole host of tasks that require an output that has more information than the input, like image super-resolution, translating doodles into images, etc.
* Models with multiple correct outputs per training example need generative models to train correctly (?)

### Terms I didn't know

* Model-based vs model-free RL algorithms: model-based = contains a generative model.
* Maximum likelihood: if we define a probability distribution, we can use that distribution to assign a _likelihood_ to our training set. Maximum likelihood is to choose parameters of this distribution that maximize this likelihood.



python cpu profiler
valgrind on cpython
pypi - JIT, metacircular, high perf compiler
ceval.c
hpat

interpreted vs JIT

cprofile will give a flamegraph - super noisy, it'll suck
would have to recompile python if i was gonna use valgrind
