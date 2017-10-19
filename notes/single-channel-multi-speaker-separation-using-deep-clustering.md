## [Single-Channel Multi-Speaker Separation using Deep Clustering](http://arxiv.org/abs/1607.02173)

_Jul 2016_

tl;dr: This paper improves generalization of [Deep clustering: Discriminative embeddings for segmentation and separation](http://arxiv.org/abs/1508.04306) by improving regularization, larger temporal context, a deeper architecture, and a postprocessing smoothing step.

#### Key ideas

* Solving the cocktail party problem has been the holy grail of speech processing and has remained unsolved for 50 years - the deep embedding approach is the closest we've come yet. This paper polishes its results.
* Regularization used: dropout.
* Curriculum learning: starting training with shorter segments, which are easier to learn discriminative embeddings for, eases the later task of learning embeddings for longer segments (which are more accurate).
* Postprocessing: two BLSTM do... something.

#### Notes/Questions

* More sophisticated regularization techniques have been introduced for RNNs since dropout. Did the authors consider layer norm?
* I suspect that classification accuracy would be improved by learned window sizes instead of a fixed window size - Hierarchical Multiscale Recurrent Neural Nets might be of interest if computational cost isn't an issue.
* Afterwards, the authors train postprocessing layers to improve signal fidelity. This sounds like a deep learning version of the optimal cover criterion in [Learning Hierarchical Features for Scene Labeling](http://yann.lecun.com/exdb/publis/pdf/farabet-pami-13.pdf)
