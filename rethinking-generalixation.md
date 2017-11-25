## [Understanding deep learning requires rethinking generalization](https://arxiv.org/abs/1611.03530)

_Nov 2016_

tl;dr: Traditional theory says DNNs should learn by memorizing, and look, we can memorize tons of labels. So why the F do they work well in practice? DNNs can learn by memorization, but they don't. The mystery is in discovering why they tend to not memorize, and instead learn functions that generalize to new data. Part of their argument consists of showing how conventional analyses of generalization can't explain this behavior, hence the need for "rethinking generalization."

#### Key ideas

* From another paper: massive memorization plays a big role in learning:

> "This leads us to believe that these models may very well make use of massive memorization when tackling the problems they are trained to solve. It is likely that learning in the traditional sense still occurs in part, but it appears to be deeply intertwined with massive memorization."

This paper disagrees: when we remove the ability to memorize, we don't hurt their ability to learn.

> In fact, our results suggest the opposite. We find that regularization can greatly reduce the ability of the model to memorize noise. If you combine that with the results from Brain, where they find that regularization doesn't improve performance very much, this suggests that DNNs are alreadynot learning by memorizing, because removing their ability to memorize doesn't hurt their ability to learn.

* NNs can overfit, even with random noise. This was still the case when they scrambled the images! Eventually all things were memorized.

* For linear models, SGD always converges to a solution with small norm
