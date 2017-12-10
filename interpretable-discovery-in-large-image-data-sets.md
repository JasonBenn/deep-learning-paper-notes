## Talk: Interpretable Discovery in Large Image Data Sets

Automated detection of new, interesting, unusual, or anomalous items within large data sets has great value for applications from finance (e.g., fraud detection) to science (observations that don’t fit a given theory can lead to new discoveries). In particular, novelty detection in image data sets could help detect new near-Earth asteroids, fresh impact craters on Mars, and other key phenomena that might otherwise be lost within a large archive. Most image data analysis systems are turning to convolutional neural networks (CNN) to represent image content due to their success in achieving high classification accuracy rates. However, CNN representations are notoriously difficult for humans to interpret. In this talk, I will discuss a strategy that combines novelty detection with CNN image features and yields interpretable explanations of novel image content.

Mars orbiting camera: over 1M images, each over 1G of size.

Novelty detection:
* clustering: look for observations that fall between clusters
* Isolation forest: build a RF, then look for examples that split off early from the main data mas
* density-based (e.g., local outlier flow)
* Use SVD to create a low-dimensional feature space, project your data down to that space and back, and anything you failed to reconstruct is an anomaly that your model didn’t capture
* DEMUD: SVD-based + explanations

Incremental SVD. Huh. Kind of like finding clusters, but with SVD - do SVD on a single example, then find the data point that’s farthest away from that model, then recompute SVD, then find a point farthest away from both of those, etc. Cool.

Especially good for discovering rare classes.
"Explanations justify selections."

DEMUD for images: using CNN representation features

But how do we interpret 1024D representation?
Two ways:
Deep Goggle: generates input that yield same feature values.
Getting SVD residuals: this means we’re looking at whatever’s in the image that’s interesting, not the actual image.
Then, reconstruction loss with this vector.

Fast discovery of novel images + visual explanations.
