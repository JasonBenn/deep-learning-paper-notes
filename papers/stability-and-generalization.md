## [Stability and Generalization](http://www.jmlr.org/papers/volume2/bousquet02a/bousquet02a.pdf)

#### Recommendation:

> "Here's an old beautiful idea that subsumes all the other generalization tricks"

#### Reply:

If I skimmed this correctly, the author doesn't attempt to derive generalization bounds for anything more complex than an SVM, for which VC dimension/Rademacher complexity still work OK (they're terrible for neural nets). Wonder how those notions of stability apply to NNs? I do love the idea of modulating inputs and watching how it affects output - same idea is used to extract confidence estimates from NNs in Yarin Gal's awesome Uncertainty in Deep Learning.

#### Highlights, comments

> We explore here a different approach which is based on sensitivity analysis. Sensitivity analysis aims at determining how much the variation of the input can influence the output of a system.

Already love this idea - similar to how you can extract confidence measures from neural net predictions. But first blush reaction is that minimizing this variation might lead to overconfidence, not regularization.

> The outline of the paper is as follows: after reviewing previous work in the area of stability
analysis of learning algorithms, we introduce three notions of stability (Section 3) and derive bounds on the generalization error of stable learning systems (Section 4). In Section 5, we show that many existing algorithms such as SVM for classification and regression, ridge regression or variants of maximum relative entropy discrimination do satisfy the stability requirements.

> This means that, in order to be stable in the sense defined above, a learning algorithm has to
significantly depart from an empirical risk minimizer. It thus has to accept a significant number of training errors (which should however not be larger that the noise level). In order to generalize, these extra training errors will thus be compensated by a decrease of the complexity of the learned function. In some sense, this is exactly what regularization-based algorithm do: they minimize an objective
> function which is the sum of an empirical error term and a regularizing term which penalizes the complexity of the solution. This explains why our approach is particularly well suited for the analysis of such algorithms.
