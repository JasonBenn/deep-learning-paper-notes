## [Deep Convolutional Neural Network Design Patterns](http://arxiv.org/abs/1611.00847)

_Jun 2017_

tl;dr: The authors do a survey of conv nets and come up with the following design patterns:
1. Architectural Structure follows the Application
2. Proliferate Paths
3. Strive for Simplicity
4. Increase Symmetry
5. Pyramid Shape
6. Over-train
7. Cover the Problem Space
8. Incremental Feature Construction
9. Normalize Layer Inputs
10. Input Transition
11. Available Resources Guide Layer Widths
12. Summation Joining
13. Down-sampling Transition
14. Maxout for Competition

#### Notes/Questions

* Sounds like freeze-connections lead the net towards greater codependence - remember that analogy from dropout about being inspired by sexual reproduction, and how it leads to fewer errors compared to asexual reproduction, because genes didn't need to all make it to the next generation in sets? If this were the case, we'd see the net train quicker but potentially at the expense of generalization power.
* "Which architectures or parts of architectures seem elegant" seems like the wrong metric to incentivize here. "Worse is Better": ease of use always trumps the elegance of the implementation.
* "Design Pattern 4: Increase Symmetry is derived from the fact that architectural symmetry is typically considered a sign of beauty and quality" worst reason ever
* "Design Pattern 6: Over-train includes any training method where the network is trained on a harder problem than necessary to improve generalization performance of inference" I like this idea - any examples? They don't cite any.
* "Cover the problem space" is good advice - if your test set or application will involve night scenes, make sure your training data includes them or augment your data.
* "ResNets can be considered to be an exponential ensemble of networks with different lengths" is an awesome observation. What ensembles would we expect to see success? That's where we should put residual connections. Skipping too many features might be overly confusing.
  * I wonder if dual residual connections work? I could imagine VGG L5 feeding in from L4 and L2, for example. We actually talked about this once in a past club I think. Could learn combos of high level, high receptive field + low level, low receptive field features. This is probably what Inception does, eh.
  * I also wonder if this could be used as a key for network compression. List all the paths you want through your network, and algorithmically determine the skip connections that will lead to the minimal networks size for those paths.
  * I wonder if it would be possible to measure the utilization of nodes in the network by some measure of compressibility. If the net were highly compressible because many of the weights weren't being used, then you've made your net too wide (or too deep). Although visualizing channel utilization is a little different than visualizing how impactful each layer is... right?
* "Make each layer's 'job' easier" isnt intuitive to me. Is this to maximize the usage of the layers inside long skip connections, who might otherwise be redundant? Does this lead to smoother gradients with fewer peaks and valleys? That might be a cool thing to measure, actually.
