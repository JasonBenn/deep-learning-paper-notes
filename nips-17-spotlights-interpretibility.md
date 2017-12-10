## NIPS 2017: Interpretibility spotlights

### Causal Generative Neural Networks

Find causal DAG between observations. Find the graph that minimizes Maximal Mean Discrepancy (Gretton et al 2007). Nonparametric (an advantage?), but expensive.

### Detecting Bias in Black-Box Models Using Transparent Model Distillation

Do model distillation on both predictor (risk score for a loan) and actual outcome (did they really default?), and detect differences between them (which would indicate bias!). For certain race categories they didn’t agree! Found bias.

### The Doctor Just Won't Accept That!

Doctors won’t just accept that the neural net thinks a patient has cancer. We don’t have a very clear API for interpretibility - what are the deliverables? Who is the stakeholder, what do they want, and does what you’re building serve them?

### Globally Optimal Symbolic Regression

Find a mathematical expression that represents function Y. Formulate as mixed-integer non-linear programming fomulation and solve it with global optimization solvers. Using images of pendulum: rediscovered pendulum periodicity formulas.

### The role of causality for interpretability.

Common cause theorem: if two random vars are statistically related, there could be a single common cause explaining both.

Ways to establish causality:
Intervention on a: raise the city, find that temperature changes. Therefore, altitude causes temperature.
* But that’s impractical, of course.
* Hypothetical intervention on a: we’d still expect it to work, because p(t|a) still applies no matter p(a) (what altitude we’ve got) - we believe there’s a physical mechanism that works here.
* We also expect p(t|a) (hypothetical mechanism) to be invariant no matter where we are in the world.

Goddamn, this talk was boring.
