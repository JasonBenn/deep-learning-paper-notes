## [Artistic Style Transfer For Videos](http://arxiv.org/abs/1604.08610)

_Apr 2016_

tl;dr: neural style transfer for videos is mostly just neural style transfer on each image + a penalty term for diverging too much from the previous frame, but there are lots of little tricks to make them look good: penalize deviations along "optical flow", don't penalize disoccluded spots, don't let artifacts at the frame edges form.

This was a really awesome paper - they had a great (if obvious) result but continued pushing and synthesizing past research to produce high quality videos.

#### Key ideas

* Single image neural style transfer has a penalty term with two components: a style loss term and a content loss term. Style loss is computed by correlating similar features (using a Gram matrix) for the generated image and comparing that to the same process for a source style image, like Starry Night. Content loss is computed via MSE between activations of deep layers.
* This paper adds a feature to make the above process look smooth in videos: they add temporal constaint that penalizes deviations between adjacent frames. They're clever about it, though:
1. they use "optical flow", and penalize deviations along "point trajectories" instead of pure deviations
* They also added several innovations to produce more coherent videos:
1. Previously occluded regions are excluded from the penalizer so they have time to rebuild.
2. Long term motion estimates additionally can help disoccluded regions remember their patterns from before they were occluded
3. Artifacts at the edge were reduced with a strategy of processing video frames in an alternating forward/backward flow.
