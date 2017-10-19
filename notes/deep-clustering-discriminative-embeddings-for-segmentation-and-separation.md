## [Deep clustering: Discriminative embeddings for segmentation and separation](http://arxiv.org/abs/1508.04306)

_Aug 2015_

tl;dr: audio clustering, even with just a few labeled overlapping human voices, is difficult. The strategy here is to learn embeddings of overlapping 32ms windows of sound, which approximate an affinity matrix that transforms connected data like spectogram samples into dense clusters that can be grouped using k-means.

#### Key ideas

* We can learn an affinity matrix; such a matrix changes the basis of our data such that it's amenable to simpler central clustering (such as k-means).
* How do embeddings estimate the affinity matrix?
* What is the objective function? Similar to word2vec, which creates similar vectors for pairs of words that appear often together, this function creates similar vectors for elements of the same partition.
* When class data exists, class-based approaches to clustering audio are great. But real world audio doesn't have labels, and generative models don't scale up or generalize super well - they're too computationally intensive. Humans, on the other hand, can segment sounds without knowing what they are, so we should invest more in the partition-based clustering approach.
* Embeddings are learned with bidirectional LSTMs.

#### Notes/Questions

* The task is hard when multiple speakers talk over one another, and even harder when the voices are of the same gender. This suggests to me that clustering applications may be more effective when used on audio mixing sources that sound very different from each other, like drums/guitar/voice in a song.
* The embedding dimensionality used here is low compared to what I've seen in NLP (which makes sense) - authors used 5 to 60 dimensions. 5 fails, but 20, 40 and 60 perform similarly.
* For reference, Gaussian process models for voice transformation tasks parameterize voice with ~40 parameters.
* Authors tried a variety of hyperparameters, which to me suggests that they had difficulty getting this net to converge at first.

#### Words I didn't know

* Spectral clustering: cluster data that is connected, but not necessarily conveniently grouped into a small area. Compare to central clustering, which is solveable by something like k-means or cosine similarity.
* Affinity matrix: the key to clustering connected but not dense features is to find a good affinity matrix. This matrix will project your data into a space in which the features _can_ be centrally clustered.
!()[https://charlesmartin14.files.wordpress.com/2012/10/spec.png]
* Laplacian matrix: a matrix representation of a graph, represents connections from vertices.
* Class-based segmentation: Segment labels are classes like grass, mountain, dog (for images). These labels are placed in the general vicinity of the entity.
* Partition-based segmentation: segment labels are bounding boxes (like a rectangle that contains a fish).
* Window function: a function that smoothly clips the edges of a signal to some width.
* Hann window function: a smooth window function.
