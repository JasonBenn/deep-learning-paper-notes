## Inductive Representation Learning on Large Graphs

GraphSAGE: an algorithm for graph representations that scales to billions of nodes.
Problem: different nodes in a graph have different numbers of neighbors - so how do you efficiently batch these things on GPUs?
Insight: random sampling with replacement so everything has 3 neighbors. (With replacement so gradient estimates are unbiased)

models.py#254
def sample:
* Input_nodes: nodes in our batch we want
* Num_layers: depth. 2 or 3 layers is always sufficient for a node’s neighborhood. (5 nodes is usually diameter of most graphs, so not helpful to increase much)
* Sample_sizes: (3, 3) 3 nodes at layer 1, 3 nodes at layer 2
* Adjacency matrix: goal is to represent as much as possible in dense formats, avoid sparse matrices. Adjacency list, but randomly padded with replacement?!

Goal is to get GPU utilization to 100%.
Whoa - tf.shuffle, as a batch, gives 5x speedup over numpy’s shuffle function - in the core algorithm these things make huge differences.
Goal is to sample fixed size neighborhoods.

def aggregate
* Samples
* Support_sizes:
* Feature_matrix: features or attributes of nodes
* Embed_dim: how big do we want generated embeddings to be

Apply an aggregation function (could be LSTM, a pooling, a mean, etc).
