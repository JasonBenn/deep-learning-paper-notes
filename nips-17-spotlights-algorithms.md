## NIPS 2017: Algorithms spotlights


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


### Premise Selection for Theorem Proving by Deep Graph Embedding

Goal: premise selection for theorem proving.
TP is basically a search problem in a knowledge base.

Classifier for relevant/irrelevant

Good representation should be invariatn to variable name
Deep graph embedding: parse tree, merge coreferences, link quantifiers and variables. This makes them invariant to var names but keeps semantics.

Neural net iteratively creates embeddings for nodes, then for the whole graph.

HolStep: theorem proving dataset with 2M+ premises/embeddings, these guys get SOTA.


### Batch Renormalization: Towards Reducing Minibatch Dependence in Batch-Normalized Models

Batch norm's surprising but important drawback: it acts differently at training and test - it can introduce bias! Especially for small batch sizes.

The reason batch norm improves speed = later layers don’t have to chase a changing distribution from earlier layers.

Read. Worth applying and using - it’s already in TensorFlow.


### Self-Normalizing Neural Networks

Turning alchemy of batch norm into electricity, lol.

Normalization techniques have a few drawbacks:
* Depend on batch size
* Computational complexity
* Learning one sample is impossible


