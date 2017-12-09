## Meta-learners for Estimating Heterogeneous Treatment Effects using Machine Learning

We have massive amounts of data from behaviors; IOT, online behavior, etc. But this data is unstructured, noisy.

Meta-learners can help you build in prior knowledge so that you can make use of this unstructured data.
Going to individual level is almost impossible, however.
 
Causality:
* On one end of the spectrum, you have physics, which mostly obeys laws that make sense. Example: Hooke’s law defining springs, etc. Sometimes causality doesn’t work - the spring might break - but it’s better than nothing.
* Statistical causal inference: trying to figure out within population if a drug is better - but these are heterogeneous effects. Would be better to figure out if subgroups are affected differently. Is there something in the middle?
Adaboost is a metalearner. You start with a weak learner, use the result, and update yourself.
 
Statistical causal inference is like a prediction problem: but predicting something we don’t directly observe and possibly can’t estimate well in a given sample.
 
Distribution of treatment effects: average might be 0, but there could be a subgroup of users that respond well and some for which the drug is harmful. “Zero average effect doesn’t mean there’s no heterogeneous effect.”
 
### About CATE
Conditional Average Treatment Effect (CATE): Individual Treatment Effect. Suppose we try to estimate this based on covariate xi. Just average treatment effect for common group. Hard part: what are the features you want to condition on.
 
Decompose MSE to approximation error and estimation error. We’ll concentrate on minimizing MSE through the estimator.
 
### Results of CATE
Social pressure experiment: send open voting record data to people via postcard to encourage them to vote. CATE gives us a significant positive group, and a small but significant negative group, even though average effect was negligible (?). Gerber, Green, Lairmer, 2008. Learned that people that have decent voting history (3 out of last 5 elections) respond best.
 
### How to estimate CATE?
Decompose CATE into several sub-regression problems. Use your favorite estimators- maybe boosting.
 
T-learner: split the data into control/treatment groups, estimate response functions separately; this is like using a forest but the first feature is a control/treament split.
S-learner: single-tree; use group as a feature, and let random forest use it (or not) to split your population.
Causal forest: kind of like s-learner but with more constraints. Goal is to have enough samples in second-to-last level groups so that you can estimate effect at leaf nodes.
 
### Definition of the x-learner
Individual treatment effect - their contribution.
Suppose you’re in the treatment group. Instead of observing the controlled outcome, we’ll compute a kind of high-grade residual for the treatment and for the control. End up with two treatment effects (?). Then you combine them to create a better estimator.
 
This method allows flexibility - you can add in prior information based on whatever effects you understand best (?).
 
There’s a tension between how well you can estimate the treatment and control group means.
T-learner is quite unbiased, but large variance; S-learner is quite biased but lower variance.
 
### Effects of effect size on ideal metalearner
For treatments with very strong effect, S and T learners perform almost the same, because S learners split very early on.
However, for treatments with a weak effect, the S-learner will win out - even over the X learner (both beat the T learner, of course - it splits way too early).
Resisting confounding: X and S do pretty well.
 
We should protect the Type 1 error rate - e.g., cross-validation, honest random forests.
 
### How do you move ML towards causality?
You need stability; if you perturb your data and dramatically change your predictions, that doesn’t bode well for causality.
It’s a minimum requirement for reproducibility, interpretation, and intervention design.
 
“Technology is just beginning to do three-way interactions”
