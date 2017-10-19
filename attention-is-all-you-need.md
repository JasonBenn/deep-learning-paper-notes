## [Attention Is All You Need](https://arxiv.org/abs/1706.03762)

_Jun 2017_

tl;dr: sequence modeling has almost always been done by recurrent nets, but within an example these techniques are unparallelizable, which is a pain for tasks with very large examples. In this paper, researchers that were motivated by the potential performance benefits of a non-recurrent (and therefore parallelizable) architecture found that a purely attentional model with this property also happened to achieve a significant improvement on BLEU scores on translation tasks.

A more detailed explanation: the meaning of the word "club" in the sentence "the ___ walked into a club" depends on its context: if the word is "DJ", that means something very different from "baby seal" (this is why word representations are often learned from the contexts in which they appear). RNNs have to process each word in sequence. CNNs can "see" far into the past or the future via convolutions or pooling layers, but the number of steps to combine information from distant parts of a sentence still grows with their distance from each other. Most current NMT models involve complex combinations of these components AND attention. This "Transformer" architecture, on the other hand, fully connects each (preliminary) word representation to all other preliminary word representations to determine how disambiguating each other word is for the current word representation, then uses a weighted average of all context words in creating final word representations (this is the encoder). The decoder similarly dispenses with RNNs by fully connecting to previously outputted words and the final word representations that the encoder created.


#### Other key ideas

* I got the vibe that the researchers were surprised by how well this architecture scores on sequence modeling tasks - like that their primary goal was performance on long sequences!

* Attentional weights are awesome for introspection and visualization - you can see what the net is paying attention to as it's building representations for each word (encoder) or generating the next word (decoder).


#### Notes/Questions

* Do encoder and decoder architectures with 6 layers (of 2-3 sub-layers) warrant residual connections? Wonder how the net performs without them - ResNet had 50-150 layers, after all.

* I would've liked to see the authors address scaled failure modes of dot-product attention for disproportionately large attentional values - their explanation makes intuitive sense, but lacks rigor.
