## A variety of representation learning/embedding papers

tl;dr:

* 12 Mar 2015, 814 citations: [FaceNet: A Unified Embedding for Face Recognition and Clustering](http://www.shortscience.org/paper?bibtexKey=journals/corr/1503.03832#martinthoma): create 128d representations of faces where distance between vectors correspond to face similarity. Loss function takes triplets of images: an image of person A (the "anchor" image), an image of person A again (the "positive example") but with a vector representation farthest from the anchor, and an image of person B (the "negative example") that is very close to the anchor; loss function needs to predict negative example. Training starts simple then increases in difficulty.


#### Words I don't know

* Large Margin Nearest Neighbor: learn a matrix that represents a basis transformation that makes target neighbors close and imposters far away.
