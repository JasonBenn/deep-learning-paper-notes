## [Pixel Recurrent Neural Networks](http://arxiv.org/abs/1601.06759)

_Jan 2016_

tl;dr: to create a decent distribution of natural images so that you can generate realistic ones, consider neighboring pixels using 2D RNNs, and approximate an ensemble of them using skip connections.

#### Notes/Questions

* The two-dimensional RNN is only conditioned on pixels above and to the left, which begs the question: why not use two-dimensional bidirectional RNNs? It's silly to think that pixels wouldn't depend on context in all directions. As for future directions - it would be interesting to imagine a context that was more local. Maybe an RNN that branched into 8 or 16 directions and considered a few steps in each of those directions, weighted by how close they are to the target pixel? Their diagonal BiLSTMs only go up and to the right as well (I think).
* "From the different parameter update rules tried, RMSProp gives best convergence performance and is used for all experiments". Why not Adam? They both incorporate per-parameter learning rate scaling, and Adam additionally incorporates momentum. (This paper was written two years after Adam was invented.) Perhaps Adam's momentum is harmful here, which might be the case if the loss function is not locally smooth.
