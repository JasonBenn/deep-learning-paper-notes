## NIPS 2017: Probabilistic methods

### Empirical Bayes Approach to Optimizing ML Algorithsm

ways to choose hyperparams (eta)
* expert knowledge
* grid search
* random sampling
* Bayes Optimization: use past results (validation error) to choose next hyperparams

you might overfit validation data
OR you pick best params and throw away knowledge learned in intermediate experiments - not optimal

hyperparam averaging

kind of like RL: action is eta, reward is 
works well!

### Doubly-Stochastic Variational Inference for Deep Guasisan Processes

GPs are priors over functions.

Posteriors are great fits if the prior is specified well.
Uncertainty about the covariance prior.
We don’t want to choose prior after seeing data - “want to be fully Bayesian”

We can stack GPs together: Deep GP.
* Degenerate: collapses as layers increase.

We propose a linear mean function.
More complex than single layer GP but without pathologies.

Using same prior, solved their motivating problem.

Novel variational posterior.

Feasible even with large datasets, don’t observe overfitting, easy to initialize (works out of the box).

### PASS-GLM

Bayesian posterior: coherent uncertainties
posterior is proportional to data likelihood times the prior.
but we have to use approximate inference, for some reason.

Large-scale bayeasian inference would ideally be scalable - would work on streaming/distirbuted data
finite-time finite-dat guarantees. if we’re apprxoimating, would like to know when it’s close to exact posterior.
would also like to get more accuracy the longer we go.
Most methods only get 2/3.

Most Bayesian models are not exponential family, which makes things easier, so we can use Polynomial Approximate Sufficient Statistics.
Approximate sufficient statistics is close in Wasserstein distance, which is nice… 
Also highly parallelizable
Can improve by considering higher order polynomial terms

Way better than online SGD to get point estimate, but this gets full posterior approximation.

### Multiresolution kernel approximation for gaussian process regression

Bayesian nonparametric ...

Guassian process regression: you estimate the posterior
How do you approximate it? Usually we use kernel functions, but these don’t scale to beyond a few thousand data points.

These guys use MKA to compute a kernel matrix. 

This is a promising approach for fast calculations of kernel matrix and its determinant, which are almost always the bottlenecks in approximating the kernel matrix.

### Multi-information source optimization

We can approximate a black-box function, but estimates are of varying quality and cost. How do join?

Multiple sources have a couple kinds of uncertainty:
* Bias. models might have discrepancy.
* Observation noise.

misoKG can solve such problems.
* Generative model
* ____

### Deep Multi-task Gaussian Processes for Survival Analysis with Competing Risks

Learning on time-to-event data. In this case, estimating risk profile. In this case, survival data.

Current SOTA is linear model that doesn’t model interactions between different causes of death.

These guys use a deep gaussian process to model interactions between different effects. 
Multidimensional random output variable.

Data augmentation scheme

### Nonlinear random matrix theory for deep learning

Why random matrices: initial weights are random. Sure, they get less random after learning, but it’s still relevant if you have an overparameterized net.

