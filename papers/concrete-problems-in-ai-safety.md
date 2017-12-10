## [Concrete Problems in AI Safety](http://arxiv.org/abs/1606.06565)

_Jul 2016_

tl;dr: in a paper that's mostly about problems in RL, one of the five problem areas is "robustness to distributional change", i.e., does our system correctly lower its confidence in novel situations? A real-world example: a medical image classifier trained on a distribution of data should make lower-confidence predictions (or opt out of predicting something entirely) when it realizes that the test set distribution is substantially different. ML systems often exhibit poor performance in such situations _and_ assume their performance was good.

#### Key ideas

* A similar problem domain: online learning with concept drift
* Well-specified models: if there is One True Distribution in the data and it can be captured with a super expressive model like a neural net, then we can make a covariate shift assumption to deal with this problem: given the relationship between p(x) and p*(x), we can make a corresponding adjustment from p(y|x) to p*(y|x). However, this can fall apart if the computed ratio is large, which is the case when p and p* aren't close.
* A more testable solution to the above: create a generative model to estimate p, and detect when it's surprised by test data. However, this approach is risky, as it's easy to mis-specify a distribution with a generative model.
* Partially specified models: if estimating the distribution is infeasible (which may often be true in nature), then use techniques that make more limited assumptions and can still perform well. For example, unsupervised risk estimation requires "positing certain conditional independencies in the distribution of errors, and using this to estimate the error distribution from unlabeled data".
* When an out-of-distribution error is detected, there are a variety of ways for an agent to react: they could prompt a human for help, abstain, or try to resolve the problem themselves by gathering more information (moving closer to the speaker, doing a low-stakes experiment by cleaning up a small amount of the mysterious chemical on the floor, etc).
