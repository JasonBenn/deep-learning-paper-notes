Bayesian Methods for Hackers - Chapter 1

[Chapter 1 solutions](https://github.com/JasonBenn/bayesian-methods-for-hackers/commit/954f4b53bc953748b72b71e5793d08ee35056303).

Key:
🔑 key point
👍 minor point
📗 vocab word
📸 flashcard
❓ Question

👍 Frequentist vs Bayesian:
Frequentist: the number of times a thing happened over a long period of time is _its_ probability.
Bayesian: probability is _my_  measure of confidence that an event will occur. Belief-based.

🔑 Bayesian analysis: good for small N. With large N, Bayesian estimates converge to frequentist estimates - the prior gets washed out.

📗 Probability density function: where the area of a distribution matches its probability mass. scipy.stats.beta.pdf

📗 Expected value is equal to its parameter.

📗 Conjugate prior: a prior that's of the same function family as the posterior. Given a likelihood function, sometimes your choice of prior will result in a posterior of the same form, this choice might make your algebra easier.

📸 Bayes' Theorem?  P( A | X ) = & \frac{ P(X | A) P(A) } {P(X) }

📗 ∈ symbol?;Belongs to set. p ∈ [0, 1], p ∈ {1, 2, 3}

📗 What's the name for a PMF where you can tune how much is on earlier numbers vs later numbers with 1 param?;;Poisson PMF. Tail extends out forever.;

📗 What's the name for a PMF that is equally likely for each of N possibilities?;;Discrete uniform distribution;

❓ Why is the prior for alpha set to 1/count_data.mean()?

❓ Why do you need to tell PyMC that some functions are deterministic? 

❓ Seems like the hyperprior of deciding the formula of your model is key (for the text messaging: that there should be two lambdas, not one, and a tau). Is there a way to determine that one choice of model leads to a set of posteriors that explain the model very well vs another choice of model?

❓ Why are np.mean(lambda_1_samples/lambda_2_samples) (.7994) and lambda_1_samples.mean()/lambda_2_samples.mean() (.7913
) different, and why is the the former better?

👍 APIs used:
@pm.deterministic: declare a function as deterministic.
mcmc.trace: get a list of values tried.
