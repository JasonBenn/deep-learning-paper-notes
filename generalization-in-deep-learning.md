## [Generalization in Deep Learning](https://arxiv.org/abs/1710.05468)

_Oct 2017_

tl;dr: another paper that tries to answer the conundrum set forth by Zhang et. all's work of 2016. Avoiding overfitting means preventing the net's ability to overfit by applying a novel penalty term that scales with the max preactivation in the final layer. A dense but excellent paper with a notable result.

#### Key ideas

* Long layout of generalization theory. tl;dr: it doesn't apply to NNs.

* Quote: architectures that work do so because we can predict what would work by looking at nature. Pretty lame.

> Meanwhile, such reasoning with Proposition 2 suggests another open question: why is it that we can often find good architectures (and other hyper-parameters) that get low validation errors (with non-exponentially-many trials relative to the validation dataset size, as in ln |Fval|/mval in Proposition 2). A close look at the deep learning literature seems to suggest that this question is fundamentally related to the process of science and engineering, because many successful architectures have been designed based on the physical properties and engineering priors of the problems at hand (e.g., hierarchical nature, convolution, architecture for motion such as that by Finn et al. 2016, memory networks, and so on)
* A neural networks with ReLU activations computes a piecewise linear function, which you could write the sum of an input-dependent set of single-input linear functions, each corresponding to an active path from an input variable to the output, where a path is "active" if no ReLU on it is in the zero-output region.

> Because the number of these paths is exponential in the depth of the network, this is not practical for doing any actual computation or even storing the model, but it is useful for doing theoretical analysis: the typical theoretical trick, which is used in this paper as in others, is to introduce some sort of independence assumption on the path activation states.

* https://www.reddit.com/r/MachineLearning/comments/76v9v4/r_generalization_in_deep_learning/doikhs4/

* New regularization term: `max(sum(abs(x), dim=0))`. Why this makes sense: large weights actually should be fine! As long as they rarely combine with inputs in a way where final layer activations are drowned out by one super loud neuron, then it's fine. Large preactivations, on the other hand, are discouraged. Takes into account weights and data. L1 reg penalizes weights.

* Cool table from paper shows that the term is doing something.

* Takeaways: simple, useful. Pros: simple to implement, comes with new theoretical generalization guarantees, nice. Cons: didn't try on other datasets; whenever I see MNIST, I wonder why they didn't try on harder datasets.



### Notes/Questions:

* The paradox presented in Zhang's paper about generalization - that neural nets can generalize and therefore it's a mystery that they don't - is essentially brushed away with logic of the form "if p then q does not imply not q then p". Not the strongest argument, considering this mystery has inspired hundreds of research papers since it was published.

* The "some data distributions are good, and some are bad" argument is also a little weak.

* Why just the last layer? Might we be hiding crazy preactivations in early layers?

* Even this is one step removed from the problem: super overconfident and incorrect predictions. Feels to me that some combination of weights and inputs is the right thing to watch out for, but by the time it's made it to the final layer, you've already passed through several activations, obscuring potentially crazy preactivation behavior in previous layers. Maybe one of your earlier layers is totally going haywire, and you don't pick it up. So why just †he last layer?

* Earlier layers could stack with later ones in ways undiscovered by training data. Worth an experiment.

* Do we still need to early stop?

* Is it helpful to make all strong weights impossible? Maybe some, but not enough to overfit, would be helpful.

* Try: stddev instead of max? Imagine if they used stddev: would penalize uneven activations (3/64 highly activated for "dog"), seems bad. Maybe better to stddev for activations past a threshold.

* Will it work for imbalanced classes? Paper only tested perfectly balanced ones.

* Reproducibility might be hard. Has anyone been able to reproduce the reported MNIST experimental results? "Ran their script with 5 different seeds, including the —best-train option, which restores the state of the RNG to exactly what the authors used for their reported results. The test accuracy fluctuates with quite a large variance between 99.60% and 99.74% during most of the training (over 5000 iterations), which is nice for the small 33x32x1024 network they use but not 99.80% as the paper reports. Moreover, only about 3.4% of all iterations has a test error of 99.70% or better. The implementation does not have a stopping condition (trains infinitely with the same fixed hyper-parameters as described in the paper). The program is using the test set for saving the best model thus far. From what I see I can only think that the reported 99.80% accuracy is a random result specific to one particular random seed and selecting the stopping iteration using the test set, which makes the result completely invalid. Even if the result could be reproduced with their seed." - https://www.reddit.com/r/MachineLearning/comments/76v9v4/r_generalization_in_deep_learning/dool07m/
