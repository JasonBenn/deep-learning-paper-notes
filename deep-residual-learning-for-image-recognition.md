## [Deep Residual Learning for Image Recognition](notes/deep-residual-learning-for-image-recognition.md)

tl;dr: The original ResNet paper.

#### Context:

* Context: deep networks cause accuracy problems: "with the network depth increasing, accuracy gets saturated (which might be unsurprising) and then degrades rapidly. Unexpectedly, such degradation is not caused by overfitting, and adding more layers to a suitably deep model leads to higher training error"

* This didn't make sense - a deep net could include a shallow net, so it should be strictly better. The later layers could literally by identities and a deep network should achieve the same performance.

* "The degradation problem suggests that the solvers might have difficulties in approximating identity mappings by multiple nonlinear layers." Translation: obscuring X makes it harder to isolate its effect on the function's output.
