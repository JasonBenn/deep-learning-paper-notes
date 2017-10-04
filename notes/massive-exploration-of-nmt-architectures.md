## [Massive Exploration of Neural Machine Translation Architectures](http://arxiv.org/abs/1703.03906)

tl;dr: NMTs are expensive to train (days/weeks of GPU time to converge), so it's hard for anyone besides Google to do hyperparameter searches. The authors test the impact of a) embedding dimensionality, b) RNN variant (GRU vs LSTM vs no memory), c) bidirectonal vs unidirectional encoders (decoders can't be bidirectional), d) depth of decoders and encoders, and residual connection variants, e) attentional variant, and f) beam search width and penalty variants.

My impression: nothing groundbreaking, but fantastic attention to reproducibility: they released code, weights, and detailed experimental results! I realized afterwards that this was written by Google Brain residents.

#### Key ideas

* Embedding dimensionality improves only slightly when you increase it from 128 up to 2048. Best tradeoff seems to be 256.
* LSTMs outperform GRUs.
* Bidirectional encoders work best.
* Deep encoders were hard to train and frequently diverged. There may be room for better normalization, initialization, or optimizer.
* Deep decoders were slightly easier to train, especially with residual connections.
* BLEU was surprisingly sensitive to the decoder's beam search hyperparameters. "Beam widths of 5 to 10 together with a length penalty of 1.0 seemed to work well", but choosing poorly often cost 1-2 BLEU (of ~22).
* Errors in early words on decoder can cascade, so it's important to get representations for early words in the encoding right. This is the chief reason why bidirectional encoders are helpful. it's also why some people try reversing the direction of words when feeding the encoder! Clever.

#### Notes/Questions

* Do small scale studies correlate well with large scale studies? this was found to be true in CNNs - the scale being varied being the size of the input image. might be worth experimenting

* Their results for multiplicative attention might not have been this bad if they scaled the multiplicative output? If that were the case, their conclusion about optimal attentional parameters might change. From "Attention Is All You Need":
> "While for small values of dk the two mechanisms perform similarly, additive attention outperforms dot product attention without scaling for larger values of dk [3]. We suspect that for large values of dk, the dot products grow large in magnitude, pushing the softmax function into regions where it has extremely small gradients 4. To counteract this effect, we scale the dot products by 1√dk."

* Why beam search specifically? There are many graph search algorithms.

* It's impressive that they ran each experiment "several" (4, I take it?) times and measured variance. I suppose this is required when an architecture frequently diverges. Perhaps better initialization is needed.

* Is BLEU the right metric? [Some researchers report](http://forum.opennmt.net/t/metrics-bleu-ppl-gold-ppl-pred/249) that SMT and NMT get similar BLEU scores even though NMT is qualitatively better, in their opinion. A bilingual person's opinion after a read through a result dataset would be interesting to see. It's also fairly sensitive to

* This is a phrase that I want to understand better: "For deeper networks, we also experiment with two variants of residual connections to encourage gradient flow"

* This one too: "Furthermore, we found that the attention-based models exhibited significantly larger gradient updates to decoder states through- out training. This suggests that the attention mech- anism acts more like a ”weighted skip connection” that optimizes gradient flow than like a ”memory” that allows the encoder to access source states, as is commonly stated in the literature."
