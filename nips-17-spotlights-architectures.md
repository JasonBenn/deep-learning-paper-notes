## NIPS 2017: Architecture spotlights


### Spherical convolutions and their application in molecular modelling

Coool - 3d convs by sliding filter over concentric spheres of different radius.
Also play with different spherical coordinate systems. Brilliant!
* Cartesian coord conv net: 50% accuracy.
* But with a spherical coordinate system: 60%!


### Translation Synchronization via Truncated Least Squares

Example: you have a distribution, you want mean.
You could sample and compute sample of mean.
But what if your sample is polluted by outliers? Mean is gross. But your mean will be closer to ground truth.
If there’s a big gap between median and mean - something’s up.

Procedure:
* delete samples that are X far away from mean
* Then recompute mean and repeat step 1 with smaller X
* Then you’ll have much smaller gap.

Using this on translation synchronization. 
Useful for: Pairwise ranking, joint alignment of point clouds, and more.

Compared to L1 minimization.


### Self-supervised Learning of Motion Capture

Goal: inverse 3d mesh from video. Mesh = Vertexes, faces.
Detailed reconstruction of human poses is helpful for AR, motion capture.

Supervised learning approach: had image -> 3d mesh. But this dataset is hard to gather.

First: train a NN with strong supervisin.
Then, unsupervised training with reconstruction loss.

SMPL: maps pose vector, shape vector to 3d mesh. This mapping is differentiable!

Inputs: 2d image.

Also SURREAL synthesized pose dataset, nice.

Self-supervised reprojection losses to finetune the model.
* 3d optical flow, projected to screen for 2d flow, then SOTA flow network.

All losses are differentiable.

Whoa, lots of tricks packed into one complicated model.


### Maximizing Subset Accuracy with Recurrent Neural Networks in Multi-label Classification

Question: which evaluation measure do we optimize? 
* Subset accuracy
* Hamming accuracy
* Micro-averaged F-measure
* Macro-average F-measure

Subset accuracy.


### Unsupervised Learning of Disentangled Representations from Video

DrNet

Disentagling
Temporally constant, temporarlly varying components.
Varying: configuration of body. Constant: background beach.

Autoencoder: 
Content encoder: 
Pose encoder: extracts time-varying
Frame decoder: takes vectors from encoders and decodes the frame.
Pose and frame get same frame, content gets different frame.

Add adversarial loss on pose feature space.
Everything that’s predictible about future frame from past frame (content encoder).

Pose encoder trained adversarially. Discourages any info about any aspects of video info that’s same across time.

Loss function: Reconstruction loss, similarity loss, adversarial loss.

Cool… could generate interesting video where just the pose is changing.

Does better than MCNet.

