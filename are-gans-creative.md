## Are GANs creative?

Generative modeling:
* you can either learn a density estimation from a bunch of samples
* you can learn an image distribution from samples of e.g. ImageNet

GAN’s Nash equilibrium: generator has to learn the data

Does that qualify as imagination?
* Imagination: “never before wholly perceived in reality” (example: generated celebrity faces)
* Is imperfect mimcry originality?
    * When generative models fail, it’s a combination of under- and overfitting.
    * These imperfections are interesting to us.

Creative adversarial networks: work on making GANs to become more original.

GANs: don’t really count as creative yet. But even so, they’re still useful to designers.

Examples:

3D synthetic eyes (that weren’t realistic enough) were passed through a refiner GAN that made the eyes look more realistic - these were then suitable as training data to a program that was going to identify where realistic eyes were pointing.

IGAN (interactive GAN): with a set of photos, your GAN can represent the manifold of all possible photos. Then you can make edits that result in realistic looking photos. Example: you can scale a shoe or paint on the shoe and the GAN will output a realistic looking shoe. Another: landscapes; user scribbles green areas, and GAN fills in the image.

Introspective adversarial network: add facial hair to photos of faces, make it look realistic.

Pix2pix.

“We can delegate the originality to the human, and rely on the GAN for the technical mastery to generate a realistic and detailed image”

Unsupervised image-to-image translation. CycleGAN is a great example. Important that it’s unsupervised (no need for identically posed horse/zebra pairs - it just learns from collection of horses and collection of zebras).

Future directions:
* Beyond realism: “discriminators currently just evaluate realism; maybe in the future they could evaluate usefulness or whether something is aesthetically appealing”
* Extreme personalization: generate designs that show fit or appeal to customer’s tastes (vue.ai)
* GAN-based simulators. Vue.ai is good enough for ads now, but not a good enough tool for designer, because it can’t help you test if it would fit poorly.

Question: how do you evaluate usefulness without human-in-the-loop?
* “Well, you would use human in the loop. The lines are blurring between generative modeling and RL communities - all are trying to maximize some kind of reward function.”

Question: what work have you seen on user interface-designing GANs?
* “A discriminator could be trained on existing designs and enforce existing designs. Or, you could imagine a differentiable user - measures if they succeed or fail, and how long it takes them to do so; this could help designers measure how well their interface is working for people”

Question: what do you care about?
* “I spend 60% on security. I spend 40% on GANs - mostly on how to stabilize the algorithm and make it easier to use.”

Question: GANs don’t work most of the time, right? (audience laughs)
* “Right now, the best thing is to wait 2-3 years and they’ll probably work a lot better. We don’t really know the ReLUs and Batch Norms of GANs, but we’ll work them out and then they’ll work a lot better”

Question: do you see GANs as a whole new type of thing?
* “I see a lot of connection between GANs and VAEs. It’s mostly L2 that I see us moving away from”

Question: thoughts on optimal transport?
* “Wasserstein GANs are used in progressive GANs. It can be really hard to tell if something works. WGANs definitely work - but the question is if someone could make the same thing work with another loss function.”
* “I know why GANs don’t work on sequences: Text is discrete, and you need the output of the generative model to be differentiable”
* “I guess if I thought images were solved, I would move on to audio next.”

Question: why do DCGANs converge so fast?
* “To be honest, I don’t know. It would be a good thing to study. They do really well with a small amount of resources along a lot of axes (training data, model size - DeepMind showed that a 1 layer generator can generate faces), but then they don’t really do much better than that. And then the last is training time. And that’s what I working on. I want GANs that do better as you pour more resources into them”
