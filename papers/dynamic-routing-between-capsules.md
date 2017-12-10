## [Dynamic Routing Between Capsules](https://research.google.com/pubs/pub46351.html)

_Oct 2017_

tl;dr: an early proof of concept that gets SOTA on MNIST (impressive!) and 10.2% loss on CIFAR10 (not as impressive). Some really neat ideas here, like reconstructive loss, rotational invariance, and outputting meaningful vectors and measuring their lengths. Hinton emphasized that the capsule idea is what's important, not the implementation.

#### Key ideas

* The loss function involves two parts: margin loss (the length of the second capsule layers' activation vectors) and reconstructive loss.
* "Margin" loss is a twist on the L2 norm of the NxD matrix output of the last layer, where N is the number of classes (10 for MNIST) and D is the dimensionality of each vector (32, in this case). By taking the L2 norm, you get a 10x1 vector, which you can then compare to the one-hot encoded label using a fancy algorithm that Hinton created.
* Reconstruction loss: pass the correct vector to decoder net, use that vector to reconstruct the input via deconvolutional layers, and calculate the squared difference between all pixel intensities. This was added to "encourage the digit capsules to encode the instantiation parameters of the input digit" (i.e., the length, lightness, line thickness, etc).
* Data augmentation and adversarial examples are an indication of a problem with convnets.
* Neat property of the output vectors: their length will be similarly high for e.g. an image of a 7 and an image of an upside-down 7, but they'll encode lots more state about the input, like their rotation; this reduces the need for data agumentation.
* A neat insight: we "see" things with a series of eye fixations, each of which identify low-level features, which we cobble together into a high-level feature. Capsules mimic this with an iterative routing process. Low-level neurons choose their parent neurons, building up a tree structure. Capsules have to be sufficiently excited to be "activated".
* Because capsules output a meaningful vector, we can measure the extent to which capsules "agree" with one another by measuring the scalar/dot product between them. Use this as the basis for Dynamic Routing, where vectors send their output to whatever higher-level capsules agree most with them. Reminds me of attention.

#### Notes/Questions

* Hinton emphasized that this is just one possible simple implementation of the capsules idea - there are many that might work.
* Is the goal of the reconstruction loss to incentivize more interpretable capsules? It's a pretty cool idea.
* You could probably take the reconstruction loss idea to any other CNN architecture - just take the last layer's activations.

#### Flashcard

* Dynamic Routing Between Capsules?;Hinton, Q4 '17;A capsule = a groups of conv filters that output a vector, compared to CNNs which output one value for feature detector. Capsule length represents likelihood of that part existing in input.<br>Margin loss: length of final capsules compared to one-hot encoded input, reconstructive loss: decode vector into image and compare to input (encourages capsules to encode meaningful features)<br>SOTA MNIST, 10.2% on CIFAR10<br>Uses attention-like "routing by agreement" idea to route low-level capsules to high-level capsules whose activations point in similar direction. Replaces pooling, where you lose tons of info;
