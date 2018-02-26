Bayesian Methods for Hackers - Chapter 2

Key:
🔑 key point
👍 minor point
📗 vocab word
📸 flashcard
❓ Question
⚙️ API

❓ This PyMC interface is odd and not very Pythonic. Why assign all variables in a context to a model instance? Lolz.

📸 What's the difference between deterministic and stochastic variables?;;Stochastic: even if all inputs and parameters were known, output would still be random (most distributions).<br>Deterministic: when inputs/params are known, so is output. Stochastic var + 1, for example.;

👍 Why bother marking deterministic functions as pm.deterministic? It doesn't change their behavior.;;Because it makes the variable "tracked by our sampling".

👍 PyMC : Theano :: Pyro : PyTorch

⚙️ theano.tensor.stack: combine separate Theano variables into one variable
⚙️ pm.Categorical: stochastic, takes a Theano variable

🔑 How should you approach Bayesian modeling? Imagine how you would generate the dataset - choose random variables with the right properties. For parameters, choose priors that either reflect total uncertainty (e.g., a uniform distribution), or skip setting them entirely (like alpha params for Poisson dsi

Poisson random variable vs poisson distribution?
