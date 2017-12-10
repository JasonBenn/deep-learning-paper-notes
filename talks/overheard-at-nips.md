### Overhead at NIPS '17

_On intra-attention and autoregressive CNNs replacing everything that RNNs can do today:_
* "They won't exceed performance of LSTMs, but that doens't mean they won't work."

_Attention over very long sequences:_
* "At a certain length, turn it Markovian. It's variable length before that, fixed length after"

_On the lifespan of RNNs:_
* "A 1-layer RNN gives you an infinite amount of nonlinearities. But with attention and convolution you have fewer nonlinearities"
* "LSTMs are still more robust compared to convolutional architectures - anecdotally, I see this for small models and small numbers of parameters. I want to understand why"
* "RNNs are dead - give it a year”
* "There are certain things that need RNNs- streaming/online learning, for example"
* "Also - counting requires RNNs"
* "Quasi-RNNs - let's not call them RNNs. They work as well as RNNs and they're faster and nobody's using them. Underrated"
* "Very shallow (RNN) models seemingly seem more robust. Shallow CNNs/attention still need lots of gradient"


_On training:_
* "If we're going to large batch settings, Monte Carlo makes a lot of sense. They're kind of magic for that."
* "Pixelwise adaptive computation time"
* "We spend 100k times more compute on training than on test"
* "If you really want to measure how well you're doing, we need to do a bang-for-the-buck change to the metrics"


_Discrete variables:_
* "Discrete latent variables could capture things we care about [learning discrete boundaries in language modeling or other hard alignments]"
* "Straight-through estimation is disgusting, but it works. You just pretend that your discrete variables aren't."
* "One place where discrete variables are useful are conditional computation"
* "They make it much easier to model hierarchical sequences."
* "[summarizing a paper] We could do a discrete latent variable to decide when to stop... but we don't like them, so instead we're going to use a very weird distribution"


_On Alex Graves magic:_
* "Gumbel sigmoid (kinda worked) or REINFORCE (couldn't get it close). His remainder distribution thing totally does work."


_On dense nets:_
* "DenseNet: rated just right"
* "If you can squeeze it in to memory, then it's the right choice. Or if you can prune them"
* "Most general prior over models" "Mmm - what about branching out and branching in?" "I don't think you actually need branching out and branching in"
* A profound thought about reparameterizing a sequence as a DenseNet; one is far better to optimize? "Whoa. Why are two linear layers better to optimize?" "I don't know."


_On other architectures:_
* "Hypernetworks: they're kind of like attention. You're reweighting the weight matrix"
* "ResNet as an ensemble of smaller ResNets. Super underrated."
* "ResNext, but I don't know if people follow that computer vision stuff"
* "[Pixelwise adaptive computation time]"


_On negative results:_
* "[repeatedly] I tried that - it didn't work."
* "We need a negative results therapy circle" "Or an anonymous forum for negative results"
