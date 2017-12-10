## What’s so Hard About Natural Language Understanding?

We’re super good at text and NMT because there’s already so much paired text.
Where can we get the right datasets for NLU tasks?
* Web-scale conversations?
* Web-scale structured data?

### Conversations data
There’s lots out there: just Twitter has 500M conversations every month.

Noisy channel model. Mapping phrases to one another.

### Likelihood doesn’t work for conversations
Maximizing likelihood makes sense for translation… but saying the least surprising thing doesn’t work as well for conversations. Examples: Google’s early inbox reply system frequently (and problematically) replied “I love you” when it wasn’t sure.

Conversations where you just reply to a question with a fact (“I’m 16”) can kind of kill the conversation. We should probably care more about choosing replies that maximize long interesting conversation.

Long-term conversation success policies (RNNs init’d w max likelihood weights) can work better
RNN reads current conversation up to a point, and this representation is state for a deep RL model.
Trained to maximize long-term success of conversation instead of likelihood.
To do that: policy gradient methods.
Policy defined by parameters of encoder/decoder of RNNs. 
Can initialize policy with maximum likelihood (as opposed to Q learning) so we can start off with meaningful responses and fine tune from there.

### Choosing reward signals
A learned disciminator (GAN), of course. 
Adversarial learning for neural dialogue. (Li 2016)
Discriminator: real or fake conversation?
Trained with REINFORCEment learning (williams 1992).
In practice, this is hard, so they go back and forth between adversarial/RL objective and ML objective, and this works well enough.
Read.

Are fluent conversations really the answer to NLU? Idk.

### Learning from web-scale structured datasets
Learning from distant supervision.
Example: time normalization. SOTA time resolvers: TempEX, HeidelTime, SUTime, UWTime. Mostly rule-based, or small dataset supervised learning.
Goal is to do this with distant supervision.
Dataset: huge database of events. And around the time that this was happening, there were tons of social media events (example: Mercury passing across the Sun). 
Multiple Instance Learning Tagger (Hoffman 2011). Deterministic OR + max likelihood; but this assumes that every tweet will contain temporal information. One solution is to split the latent variables into entities mentioned in text, and encourage agreement. 

### Where can we find large open-domain NLU datasets?
Twitter events for time normalization
Billions of internet conversations

Maybe we should start from the datasets and design models for the data instead of starting with the model and looking for data.










