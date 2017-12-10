## [Generative Adversarial Nets: An Overview](https://arxiv.org/abs/1710.07035)

_Oct 2017_

tl;dr: a recent survey paper of GANs architectures and uses.

#### Key points:

* GANs are excellent for estimating data generating distributions.
* Interesting architectures: LAP-GAN, DCGAN (uses strided convolutions in generator, fractionally strided convolutions in discriminator), conditional GANs (class-conditional nets, resulting in less uncanny results for multi-label datasets), InfoGAN (by maximizing mutual information between the generator output and a "latent code" extracted from the noise source), GANs that include inference networks that allow a user to convert existing images to latent encodings like BiGAN, and GANs which are used as a training objective for an autoencoder instead of KL divergence (AVB).
* GAN use cases: image synthesis, superresolution, image-to-image translation, tasks that involve any of the pieces of the GAN after it is trained (fine-tuning the discriminator network and repurposing it for classification, for example)
* Problems with GANs: generators commonly produce a small number of samples that the generator is unable to distinguish (mode collapse), and training instablity (optimal solutions exist at saddle points instead of at local minima, which gradient descent can't always find, so second-order optimization techniques are required, but these are computationally expensive).

#### Notes/Questions

* How do we evalute the quality of a data distribution?
* How does the latent code from InfoGAN compare to the learned encoding from BiGAN? Which encoding is more interpretable?
