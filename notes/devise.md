## [DeViSE: A Deep Visual-Semantic Embedding Model](https://research.google.com/pubs/pub41869.html)

tl;dr: Instead of topping a convolutional net off with a softmax layer that predict ImageNet category, top it off with an FC layer to the image's label's word vector. Train the word vectors and image representations separately, assemble the entire model, and fine tune.

#### Key ideas

* The loss function choice was important. They tried two approaches:
  * calculating absolute similarity between the model output and the target word vector via L2 loss, as recommended by Socher [18]
  * evaluating if the output vector was more similar to the target word vector than other, randomly chosen word vectors.
* The latter turned out to be _twice_ as accurate as the former. This makes sense - KNN is a ranking algorithm, so it makes sense that a ranking-based loss function would work better than an absolute similarity-based loss function. After all, they don't care that the vector generated for an image of the royal family is pretty distant from the word vector for "king" - just that it's a closer vector than all the clearly unrelated word vectors.
* You can build really cool things when you've connected images and words/phrases into the same feature space.

#### Notes/Questions

* Publically available word vector datasets have improved since this paper was published in 2013. They used 155k word and phrase vectors mined from 5.4B words from Wikipedia. Now, [word2vec](https://code.google.com/archive/p/word2vec/) has a 3 million word/phrase dataset trained on part of a 100B word dataset from Google News. However, word vectors in the DeViSE paper were 500 or 1,000-dimensional, whereas the Google News dataset is 300-dimensional - so while the dataset is much larger, gains are probably offset by using lower dimensional word vectors.

* How does this architecture compare to a VAE with a loss term measuring the KL divergence between an image encoding and the image's label's word vector? This architecture is much more amenable to transfer learning, for one.

* TIL: "Cosine similarity between vectors is used for measuring semantic similarity. Unit-norming the vectors and using dot product similarity is an equivalent similarity measurement."

* This would make visual equivalents of the famous word2vec analogy examples (king - man + woman = queen) possible.
