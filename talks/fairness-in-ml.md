## Fairness in ML

* Framing of problem
  * Technical kinds of bias
    * Selection/sampling/reporting bais
    * Bias of estimator
    * Inductive bias
  * What kinds of bias are ethically concerning?
    * Practically irrelevant concerns, of course, like race, gender
    * But also moral relevance: not morally permissible to discriminate against the disabled, for example, even though they might cost more to accomodate.
    * Legally recognized protected classes:
  * Disparate treatment
    * Intentionally (or not) treating people differently.
  * Disparate impact. What _legal framework_ proves that the model discriminates? 20% difference, where there exists a better model.
    * Does this model result in an unfair distribution of outcomes?
    * Established by 4/5ths rule: is there a 20%+ difference between different groups along one of the protected dimensions?
      * If so, you need to offer a justification for this.
      * Defendent can argue: "Business necessity" or "job-related"
    * Plaintiff then has opportunity to show _alternative_ practice
  * Tension between these two: Ricci v DeStefano.
    * In a correction for disparate impact, white students were no longer going to get promoted, so they sued for disparate treatment!
  * Incidence of discrimination
    * Callback rate for white names vs black names: 50% higher for white names
  * _
    * Skewed samples can reinforce themselves
    * Learning to predict hiring decisions:
      * Problematic, this will reinforce what human decisionmakers are doing
        * PROBLEM. Are we legally exposed to disparate treatment if we approximate a biased dataset?
    * Limited features
      * Be careful of measuring with accuracy - might trample on accuracy for minority groups. *Break out precision and recall for each minority group*, watch for 20% differences in protected statuses.
      * Lots of features correlate with protected features, shit. Sufficiently rich data will approximate these features.
    * Legal exposure
      * Bottom line: nobody is using ML for disparate treatment, so disparate impact is clearly the vulnerability
      * However, for a disparate impact argument, a defense of "this is what's in the data" is generally satisfying for the court.
* Formal definition of problem
  * Notation
    * X = features of individual (e.g., browsing history)
    * A = sensitive attributes (gender)
    * C = c(X, A) = (learned predictor: show ad or not)
    * Y = target variable (is this person a SWE)
  * Three fundamental criteria
    * Independence: is C indep of A (sensitive attr)
    * Separation: C indep of A cond on Y
    * Sufficiency: Y indep of A cond on C
  * Achieving independence
    * Preprocess data so that C and A are totally independent.
      * Interesting. Representation learning.
      * Zemel et al, "A Fair and Rich Z"
      * Minimize mutual information between sensitive attrs
  * Shortcomings of independence
    * Rules out perfect predictor C = Y. Ignores any correlation.
      * Females predicting SWEs.
    * Permits laziness.
      * Gets qualified people from one group, random from another.
        * Whoa - would be good to measure this.
        * "Allows to trade false negatives with false positives"
  * Achieving separation
    * Definition, properties
      * R and A, even when conditional on Y, should still be indep.
      * Nice! Penalizes laziness. Incentivizes groups to have similar errors.
    * Post processing for a binary classifier. _Choose intersection of ROC curves._
      * ROC curve. Worth maximizing, bounded away from main diagonal.
        * For a given threshold, what is the given true positive rate vs false positive rate?
      * Plot 2 ROC curves, one for A, one for B, take the intersections
        * These are tradeoffs that are achievable for each group!
        * Choose the intersection, that's where tradeoffs are the same
    * Properties:
      * If you start with something close to optimal, this will keep you pretty close to optimal.
        * If you're not, collect more data.
      * Woodworth-Gunasekar-Ohannessian-Srebro (17)
  * Sufficient
    * Definition
      * In graphical model - R sits between Y and A.
      * For the purpose of predicting Y, we don't need to see A.
        * "R is sufficient for predicting Y"
      * For loans, ideally credit score would be sufficient for predicting creditworthiness. Wouldn't need to look at race.
      * Helpful for interpretibility, too.
    * Calibration via Platt scaling is one cool way to achieve this.
  * Any two of these are mutually exclusive (except in degenerate cases)
    * So tradeoffs are necessary to consider
    * Simple tradeoff:
      * Sufficiency: equal precision in two groups
      * Separation: equal recall in two groups
      * Not sure if I have this right ^
* Drawbacks
  * Corbett-Davis, Pierson, Feller, Goel, Huq '17
    * Calibration is insufficient to rule out unfair practices
    * ProPublica v COMPAS... some caution necessary
      * Arrest more low risk individuals = parity of detention/FPR rates
  * All criteria so far are observational... passive
    * No _what if_ or _interventions_
    * Definition: anything involving features X, A, classifer C, outcome Y.
* Real world examples
  * Scenario 1
    * gender bias applies to programmers. A influences Y.
    * A influences if you visited Pinterest.
    * Y influences if you visited Github.
    * Bayes optimal predictor R will use both of these features.
    * Optimal score: look at Github and Pinterest features.
    * Optimal separated score: won't use Pinterest feature, because it's correlated with protected attr gender.
  * Scenario 2: find slides.
    * Optimal score: look at just CS degree.
    * Optimal separated score: actively subtract out bias in computer science by explicitly looking at gender and correcting for that.
  * Causal graphs as the answer to some problem with the above distributions
    * Result in same probability distribution. This is distressing somehow, and solution requires causal reasoning.
    * Scenario 1: Pearl's analysis of Bickel's UC Berkeley sex bias study
      * Gender bias in admissions _explained_ by influence of gender on department choice: women chose more competitive departments.
      * We might decide: This path through a causal graph is OK.
    * Scenario 2: we might decide that less women in CS is an OK path.
    * Scenario 1: we might decide that path to gender through Pinterest feature is not OK.
* Interventions
* Counterfactuals
  * What would've happened had I been of a different gender when applying to this job?
    Counterfactual fairness: Russell, Kusnes Loftus Sliva '17, see them at poster session on Weds.
* Hierarchy of possibilities for analyzing problems...
  * Inspect meaning of features: no causal inference necessary
  * Inspect paths in causal model: we might have qualitiative causal udnerstnading
  * Estimate average causal effects: causal inference and assumptions (not easy to do)
  * Estimate individual level counterfactuals: requires faith in model or strong quantiitative causal understanding
  * ^ Not a silver bullet! Requires increasingly strong model and assumptions.
  * Example
* Construct space (grit, intelligence) vs observed space (Duckworth grit tests, IQ tests) is as important as distance from observed space to ___ space
  * Enter measurement theory: Hand (2010)
  * Did I hear something about a compiler that would refuse to compile if it detected unfair statistical measures in violation of above constraints? Whoa.
* "Construct validity"
  * How do you decide if a measurement (IQ) is valid for a construct (intelligence)?
    * Content: do test items appear to be measuring them? _Asking Dept of Grit if they think test makes sense._
    * Substantive: is construct supported by sound theoretical foundations?
    * Structural: does score reflect relationships in construct domain?
    * External: does score predict external target variables?
    * Generalizability: does score generalize across groups?
* Conclusions
  * Observational criteria: can help discover discrimination, but are insufficient on their own.
    * There is no conclusive proof of fairness - maybe we should move on from the word "fair"
  * Causal viewpoint can help articulate problems and organize assumptions.
  * Social questions start with measurement - interrogating features is just as important as scrutinizing model.
  * Human scrutiny is irreplaceable.
* Recommendations
  * Besides inspecting models, watch data and how it was generated
  * Study long-term effects, feedback loops, interventions
  * Establish qualitative understanding of when/why ML is the right tool
  * Establish understanding of what constitues negligence

* Terms I didn't know
  * bottom (upside down T) = independence
  * Graphical models
    * Can represent conditional independences
  * Laziness
  * Nonparametric model
    * Kernel methods

* Takeaways:
  * Obviously don't use race/sex as predictive feature.
  * Be careful of measuring with accuracy - might trample on accuracy for minority groups. *Break out precision and recall for each minority group*, watch for 20% differences in protected statuses.
  * Legal exposure
    * Bottom line: nobody is using ML for disparate treatment, so disparate impact is clearly the vulnerability
    * However, for a disparate impact argument, a defense of "this is what's in the data" is generally satisfying for the court.
  * Ensure fairness between groups by achieving separation.
  * Check out this tool: research.google.com/bigpicture
  * Papers:
    * Paper session on fairness is Weds at 6:30pm - 10:30pm.
    * READ: On Fairness and Calibration.
  * A good blog post might highlight:
    * Highlight relevant law, whether things are _morally relevant_ (vs statistically relevant)
    * Measure if bias is present between various groups
    * How we achieve separation and/or separability between protected statuses.

* Questions:
  * What is the difference between disparate treatment and disparate impact?
    * Disparate treatment is where the rules applied are not neutral. Disparate impact shows that the model is biased even though the rules are neutral.
  * What is precision?
    * Precision is the number of true examples identified as a % of all example identified. % correctness of predictions.
  * What is recall?
    * Recall is the number of true examples identified as true as a % of all true examples. % of truth captured.
  * What is the difference between separation and sufficiency?
    * Legend: feature X, sensitive feature A, predictor C, output Y.
    * Separation is making sure our predictor C ignores morally irrelevant random variable A.
    * Suffiency is making sure our model outputs Y just as well with X and A as it does with just X. So it doesn't need A at all!
  * What is a ROC curve?
    * Sometimes your binary classifier has a confidence threshold. How do you decide where to set the threshold? You try to maximize TPR (correct diagnoses) and minimize FPR (false alarms), but both increase as you lower the threshold. ROC is a graph that measures various threshold settings.
  * What is laziness, and how does separation achieve laziness?
    * A model is lazy when it makes accurate predictions for a majority group and random predictions for a minority group.
    * Separation (requiring that your predictor ignore sensitive random var A) makes this impossible.
* Discussion questions:
  * How do we build fair representations
