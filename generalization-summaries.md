## A variety of generalization papers

* 16/12/13, Im: An empirical analysis of the optimization of deep network loss surfaces. Optimization algorithms take different paths at saddle points, reach different final weights. #optimization
    * Asks: how much of NN behavior is due to the training process?
    * Different optimizers (ie sgd +momentum vs Adam vs RMSProp ) converge to very different points in space, although they have similar accuracy.
    * https://arxiv.org/abs/1612.04010
* 17/05/24, Soudry: Train longer, generalize better. Large batch sizes (which were thought to hurt G) only hurt G because of small # of updates. #optimization
    * It has been observed that when using large batch sizes there is a persistent degradation in generalization performance - known as the "generalization gap" phenomena
    * The "generalization gap" stems from the relatively small number of updates rather than the batch size.
    * Proposed solution: ghost batch norm. Do virtual minibatches within each batch for batch norm.
    * We further investigate different techniques to train models in the large-batch regime and present a novel algorithm named "Ghost Batch Normalization" which enables significant decrease in the generalization gap without increasing the number of updates.
    * We note that in a multi-device distributed setting, some of the benefits of "Ghost BN" may already occur, since batch-normalization is often preformed on each device separately to avoid communication cost. Thus, each device computes the batch norm statistics using only its samples (i.e., part of the whole mini-batch). It is a known fact, yet unpublished, to the best of the authors knowledge, that this form of batch norm update helps generalization and yields better results than computing the batch-norm statistics over the entire batch.
    * Another confusion: Overall, they really show that popular learning rate and early stopping rules of thumb are misguided.`
        * https://www.reddit.com/r/MachineLearning/comments/6d6f8h/r_train_longer_generalize_better_closing_the/di0j0b1/
    * Corroborated by Martin, early stopping? Generalization gap modeled by his phase diagrams?
    * https://arxiv.org/abs/1705.08741
* 17/06/16, Y Bengio/Courville: A Closer Look at Memorization in Deep Networks. NNs can memorize noise, but they prefer simpler patterns first. Theory that doesn't consider datasets when estimating bounds won't work. #memorization
    * From abstract: estimating capacity without considering the dataset, which generalization theory often does, doesn't work for NNs with SGD.
        * https://arxiv.org/abs/1706.05394
        * Our analysis suggests that the notions of effective capacity which are dataset independent are unlikely to explain the generalization performance of deep networks when trained with gradient based methods because training data itself plays an important role in determining the degree of memorization.
* 17/01/23, Hinton: Regularizing Neural Networks by Penalizing Confident Output Distributions. Entropy regularization: penalize large post-activations. #memorization
    * Main difference: postactivations
    * https://arxiv.org/abs/1701.06548
* 17/03/01, Kreuger/Courville: Deep Nets Don't Learn via Memorization. Hypotheses learned for real data are simpler than for random data, so they must be learning patterns, not just memorizing. #memorization
    * Learning noise vs learning a dataset is different
        * Noise takes longer to learn
        * Time to learn random labels is harder than learning random inputs!
            * Easier to find patterns in noise when you don't have to ignore existing patterns (?)
        * Models learn simpler functions w real data than w noise
            * Measured by sharpness of loss function at convergence.
    * Inhibiting memorization (dropout, L2) hurts training accuracy for noise, but not real data.
    * "Seems to directly contradict the message in this Google Brain paper "Understanding deep learning requires rethinking generalization." - No, it doesn't.
    * https://openreview.net/references/pdf?id=H1xEzlHKx
    * https://medium.com/@phelixlau/deep-nets-dont-learn-via-memorization-6fd692dea63
* 17/10/17, Quoc Le: A Bayesian Perspective on Generalization and Stochastic Gradient Descent. Optimum batch size
    * Written quickly in response to a trend this year on "Rethinking Generalization"
    * ? what's "Bayesian Evidence"?
    * They uncovered clear, practical insights. The most important one is the linear relationship between the best performing learning rates and batch sizes, proven theoretically and demonstrated empirically.
    * We have been tuning learning rates anyway since day one. We just need to be aware of how batch size can effect things.
    * They prove how Bayesian Evidence can detect memorization, resolving the surprising behaviour observed in the "Rethinking Generalization" paper
    * https://arxiv.org/abs/1710.06451
* 17/10/25, Le: Bayesian perspective on generalization and SGD. Zhang's observations can be explained by evaluating Bayesian evidence, which penalize sharp minima. Also, figure out optimal batch size?
    * https://arxiv.org/pdf/1710.06451.pdf
* 17/10/27, Butzkus: SGD Learns Over-parameterized Networks that Provably Generalize on Linearly Separable Data. SGD avoids overfitting, even for models with more parameters than observations.
    * Cites Generalization in Deep Learning
    * https://arxiv.org/pdf/1710.10174.pdf
