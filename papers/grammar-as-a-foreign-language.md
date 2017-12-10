## [Grammar as a Foreign Language](http://arxiv.org/abs/1412.7449)

_Jun 2015_

tl;dr: SOTA on syntactic parsing using the standard seq2seq with attention architecture.

Syntactic constituency parsing (the task of assigning part of speech tags to words in a sentence) has historically required researchers to encode linguistic insights - for example, by ingesting words into a stack and delaying part-of-speech decisions.

With the success of attention in sequence-to-sequence tasks (particularly in NLP), it was only a matter of time before someone applied the same basic architecture to this task.

With LSTMs for encoders and decoders, a standard attention mechanism, a synthetic dataset trained on multiple existing parser programs, and "relatively little effort or tuning", the authors were able to exceed the SOTA.


#### Notes/Questions

* Strange how the dataset is constructed with hand-crafted parser programs, but the output of the net trained on that data (F1 score of 92.5 on the WSJ) exceeds that of the parser on the same task (90.5). How is the student beating the teacher?
  * Ah - they were clever - they selected only the sentences that were parsed identically by multiple parser programs. This dataset made up the "high-confidence corpus".

* "We only used dropout when training on the small WSJ dataset and its influ- ence was significant. A single LSTM+A model only achieved an F1 score of 86.5 on our develop- ment set, that is over 2 points lower than the 88.7 of a LSTM+A+D model."
  * It's unclear to me why they wouldn't experiment with using dropout in other experiments.

* When they initialized word embeddings with pre-trained word2vec vectors, they found a consistent small impact.
  * "The F1 score on our development set was 0.4 lower for the LSTM+A model (92.9 vs 93.3) and 0.3 lower for the LSTM+A+D model (88.4 vs 88.7). So the effect of pre-training is consistent but small."
  * It's clear that the non-pretrained model would require more training time to reach a similiar score. I wonder if they cut training time short or if their learning rate was too low by the time their model converged on its score - could a cyclic learning rate
