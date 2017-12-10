## NIPS 2017 algorithms spotlights

### Gradients of Generative Models for Improved Discriminative Analysis of Tandem Mass Spectra

Tandem mass spectomotery: identifies proteins in a drop of blood.
Take the complex sample, which has proteins, then get spectra. Protein subsequences (peptides). Then try to identify each with scorign algorithm. Peptide spectra.

PSMs are poorly calibrated, which affects classifier accuracy.
So calibrating them with a PSM fixes these PSMs.

Dynamic Bayesian Network called DRIP is typically used, create heuristic features that improve classifiers by 6%.

THIS WORK: Non-heuristic approach works much better.
“Gradient features + Fisher Kernel”

General coder that models a large class of scoring functions.
Allows unsupervised learning using gradient descent and max-product inference.

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


### Premise Selection for Theorem Proving by Deep Graph Embedding

Goal: premise selection for theorem proving.
TP is basically a search problem in a knowledge base.

Classifier for relevant/irrelevant

Good representation should be invariatn to variable name
Deep graph embedding: parse tree, merge coreferences, link quantifiers and variables. This makes them invariant to var names but keeps semantics.

Neural net iteratively creates embeddings for nodes, then for the whole graph.

HolStep: theorem proving dataset with 2M+ premises/embeddings, these guys get SOTA.

### Deep Multi-task Gaussian Processes for Survival Analysis with Competing Risks

Learning on time-to-event data. In this case, estimating risk profile. In this case, survival data.

Current SOTA is linear model that doesn’t model interactions between different causes of death.

These guys use a deep gaussian process to model interactions between different effects. 
Multidimensional random output variable.

Data augmentation scheme

### Unsupervised Learning of Disentangled Representations from Video

DrNet

Disentagling
Temporally constant, temporarlly varying components.
Varying: configuration of body. Constant: background beach.

Autoencoder: 
Content encoder: 
Pose encoder: extracts time-varying
Frame decoder: takes vectors from encoders and decodes the frame.
Pose and frame get same frame, content gets different frame.

Add adversarial loss on pose feature space.
Everything that’s predictible about future frame from past frame (content encoder).

Pose encoder trained adversarially. Discourages any info about any aspects of video info that’s same across time.

Loss function: Reconstruction loss, similarity loss, adversarial loss.

Cool… could generate interesting video where just the pose is changing.

Does better than MCNet.

Read!!
