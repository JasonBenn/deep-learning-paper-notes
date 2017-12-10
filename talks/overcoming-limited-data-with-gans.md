## Overcoming Limited Data with GANs

GANs were originally designed to produce samples from same distribution as training data - now used for lots of things.

Example: missing data.
* Badly occluded picture
* Medical data

### Semi-supervised learning
When the variable that’s missing is labels
Discriminator for N different classes: discriminator has N+1 classes (one extra for the class of all fake things)
We’re starting to use more and more label categories and smaller datasets.

Private aggregation of teacher ensembles (Papernot 2016): guarantees privacy of training data. And if you query the teacher fewer times, you get stronger privacy guarantees, so improving the performance of semi-supervised GANs is helpful.

### Set-member supervision
Specific output is a member of set of appropriate outputs.
Example: next video frame prediction. Adversarial approaches really outperform MSE and Mean Absolute Error - both of the latter make the mistake of blurring lots of futures together.

### Unsupervised correspondence learning
Can learn correspondences between different domains. Unsupervised.
Correspondence = can recover day scene from night scene.
Generated night scene should be a realistic member of set of night scenes.
Translating without parallel corpora by aligning distributions - whoa.

### Replace data collection with simulation
Example: simulating particle physics.
"If the particle actually exists, will we actually be able to find it with our experiments?”
GANs learning from Monte Carlo models and simulations can actually learn some physics - computational cost of GAN is much less than MC model.

### Simulated environments and training data
Apple wanted to solve the problem of where a user is looking; achieved this by rendering a basic synthetic eye, then passing it through to a realism-adding GAN.
GAN was trained on collection of unlabeled data.
Self-driving cars: synthesizing images corresponding to high-level segmentation mask.
Can get segmentation masks from GTA! The masks are realistic enough to work, which is awesome.
Read: “Driving in the Matrix” Sounds awesome.

### Domain adaptation
Lots of labels in one domain, but you want to solve problem in another domain.
Example: object recognition on mobile devices; but ImageNet data is professionally cropped and brightly lit.
Example: pedestrians.
Read: Domain Adversarial Networks (Ganin et all, 2015).
You train feature extractor, which learns to pick features no matter the domain; discriminator tries to identify domain. Awesome.

“Truth is easier to compress than randomness.”
