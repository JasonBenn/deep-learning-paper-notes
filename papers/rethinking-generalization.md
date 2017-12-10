## [Rethinking generalization requires revisiting old ideas](https://arxiv.org/pdf/1710.09553.pdf)

_Oct 2017_

tldr: generalization behavior is unintuitive, but it can be modeled with 2 inputs: noise + early stopping. Through their experiments, the authors demonstrate that these hyperparameters can induce surprising "phase shifts" in network performance, providing a new and clever way to empirically demonstrate network behaviors.

#### Key ideas

* NNs are confusing, people conclude that they're [sensitive/not sensitive] to noise, PAC/VC theories [are/are not] appropriate for NNs, etc.

* amount of noise added to network = decreased effective capacity of model. You're soaking up the memorization ability of the net for no gain

* early stopping (earlier = higher "temperature", a reference to statistical mechanics)

> Neural networks (NNs), both in general [1] as well as in their most recent incarnation as deep neural networks (DNNs) as used in deep learning [2], are of interest not only for their remarkable empirical performance on a variety of machine learning (ML) tasks, but also since they exhibit rather complex properties that have led researchers to quite disparate conclusions about their behavior. For example, some papers lead with the claim that DNNs are robust to a massive amount of noise in the data and/or that noise can even help training [3, 4, 5], while others discuss how they are quite sensitive to even a modest amount of noise [6, 7]; some papers express surprise that the popular Probably Approximately Correct (PAC) theory and Vapnik-Chervonenkis (VC) theory do not describe well their properties [7], while others take it as obvious that those theories are not particularly appropriate for understanding NN learning [8, 9, 10, 11, 12, 13]; many papers point out how the associated optimization problems are extremely non-convex and lead to problems like local minima, while others point out how non-convexity and local minima are never really an issue [14, 15, 16, 17, 18, 19]; some advocate for convergence to flat minimizers [20], while others seem to advocate that convergence to sharp minima can generalize just fine [21]; and so on.

* PAC/VC suggests that generalization changes gradually... but these guys show there are occasional phase changes. So PAC/VC isn't applicable.

* Quote: we'd expect worse performance when we add noise in most models:

> To understand why this seems peculiar to many people trained in statistical data analysis, consider an SVM, where this does not happen. Let’s say one has a relatively-good data set, and one trains an SVM with, say, 90% training accuracy. Then, clearly, the SVM generalization accuracy, on some other test data set, is bounded above by 90%. If one then randomizes, say, 10% of the labels, and one retrains the SVM, then one may overtrain and spuriously get a 90% training accuracy. Textbook discussions, however, state that one can always avoid overtraining by tuning regularization parameters to get better generalization error on the test data set. In this case, one expects the tuned training and generalization accuracies to be bounded above by roughly 90 − 10 = 80%. Observation 1 and Observation 2 amount to saying that DNNs behave in a qualitatively different way.

* Quote: changing generalization params sometimes make surprising step functions:

> Indeed, recent empirical evidence suggests the obvious conjecture that “every” DNN has, as a function of its control parameters, some kind of generalization phase diagram, as in Figures 1(a) and 1(b); and that fiddling with algorithm knobs has the effect of moving around some kind of parameter space, as in Figure 1(c). In these diagrams, there will be a phase where generalization changes gradually, roughly as PAC/VC-based intuition would suggest, and there will also be a “low temperature” spin glass like phase, where learning and generalization break down, potentially dramatically

#### Notes/Questions

* ? Convergence to flat minimizers [20]?
* ? Convergence to sharp minima can generalize just fine [21]?
* Could phase shift diagrams more precisely demonstrate surprising performance characteristics in other architectures, like mode collapses in GANs?
