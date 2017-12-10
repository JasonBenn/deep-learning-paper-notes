## Probabilistic Programming with Pyro

Provides for sampling from distributions, observing distributions, and learning parameters.
Pyro automates posterior inference.
Take a generative model for data, and a function
Guide towards the posterior of the model.

Variational autoencoder: Hello World of probabilistic models.

Generative model for VAE:
Register parameters in decoder with PyTorch.
Sample latent code.
Decode the latent into the parameters for the observation distribution.
Return the image from the Bernoulli distribution.

There are particular observed images.
“Don’t sample a new image - observe this image being the outcome.”

Guide goes up from images to the latent z.
Encoder: aha! I have a neural net with a lot of trainable parameters.

pyro.infer.SVI - stochastic variational inference optimizer.

T-SNE from latent representation visualization! Cool. IPython notebook and others on Pyro website - worth checking out.

MultiMNIST results are disappointing. Next step: try the Attend-Infer-Repeat model from DeepMind.

Images are made of some number of objects. Each has a “what” that describes what the thing is and a “where” that controls where it is in the image. We’ll have a latent code zwhat, a latent code for zwhere. Then, add the thing to a canvas, and repeat for the number of images you want to put on canvas.

Interlude: defining geometric distribution defined recursively with bernoulli random trials - keep sampling Bernoulli until you get a head, and once you do, return the number that you draw. So different executions of this distribution samplign function can have diff numbers of random variables.

Z_where is a 3D vector - x, y, and size.
Z_what is a 50D vector - basically the same as the latent code from the VAE.
Decode z_what into pixel space with a NN.
Then pass decoded image and z_Where to object_to_image, which puts it in image.
Stick this whole thing into a geometric distribution with an (initially empty) canvas. Whoa!

### How is a random geometric distribution parameterized?
Ah! A parameter that controls when to stop recursion!
Also need a RNN to consume hidden state from previous step to inform sampling in current step.

SVI ELBO is used to learn model and guide pair. Many terms have super high variance - by breaking down the equation, we can identify the problematic terms; if you don’t manage this then the variance of your gradients will be so high that you’ll never learn anything useful.
“Pass this flag to only include terms in this objective function that actually need to be there”
