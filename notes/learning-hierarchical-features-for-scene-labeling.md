## [Learning Hierarchical Features for Scene Labeling](http://yann.lecun.com/exdb/publis/pdf/farabet-pami-13.pdf)

_2013, cited by 1126_

tl;dr: label every pixel using a convolutional net that classifies regions of varying sizes centered on each pixel. Then, to aggregate noisy per-pixel predictions to clean predictions for whole regions, create a tree that segments areas of varying size by color similarity and choose regions and labels that minimize total entropy.

![scene labeling](http://www.clement.farabet.net/img/parsing-model.png)

These pixels can be used for image segmentation (obvs) and also scene summarization - authors explain the scene using the most salient components.

SOTA on a couple datasets and near SOTA on another, while being 10x faster. 320x240 image label in <1s.

They also featured elaborate postprocessing to smooth the noisy pixel predictions, but found that "even in the absence of any post-processing, by simply labeling each pixel with the highest-scoring category produced by the convolutional net for that location, the system yields near state-of-the-art pixel-wise accuracy, and better per-class accuracy than all previously-published results. Feeding the features of the convolutional net to various sophisticated schemes that generate segmentation hypotheses, and that find consistent segmentations and labeling by taking local constraints into account improves the results slightly, but not considerably"

#### Terms I didn't know

* What is a Laplacian pyramid, and what does an image look like after it's been transformed through one?
  * Pyramid representations are a family of image processing techniques that create multiple scaled copies of an image. Gaussian pyramids, for example, are the original image followed by e.g. 3 more images, each blurred and with every other pixel sampled, so they're each 1/4th the total resolution of their parent.
  * Laplacian pyramids have only original pixels at the bottom (smallest) image, and each larger image is a difference image. This way, you can reproduce any resolution image by adding the smallest image to any/all of the difference images. This is useful for compression (and apparently, image segmentation).
* What are "superpixels" and how do they contribute to segmentation? Are these pixels areas with clear boundaries somehow?
  * Part of the postprocessing step. Identifying every pixel as a different class is noisy - adjacent pixels will often have totally different predictions. Identify regions with similar color intensities and assign an aggregate class to each region based on the distribution of pixel classes. Thus, pixel classes follow natural color contours of the image.

#### Key ideas

* Conv net predictions at each level of the Laplacian are concatenated together. Smaller images were upsampled so that they would be matching sizes.
* Boundaries suffer from a lack of context and require postprocessing for good pixel predictions.
* Clever optimization: optimal cover. Given a distribution of class predictions, we can use entropy to measure the "impurity" of the segment. "Each pixel is then labeled by the minimally-impure node above it, which is the segment that best 'explains' the pixel"

#### Notes/Questions

* Superpixels and the purity criterion are liable to obscure rare or small image features that nonetheless would be important to classify.
* How does the purity criterion perform compared to counting the pixels of each class within a superpixel region and taking the argmax? Is the extra complexity worth the benefit?
