## Exploring the different paths to achieving disentangled representations

Siddharth et all ’17: Disentangled Representations…

What is a good way to represent scenes?

What do good representation have?
* Instance complexity should be appropriate.
    * Example: a scene with one person requires pose for 1 person; this is less complex than a scene of a crowd.
* Conditional attributes
    * Car might just be described by model and orientation
    * Human would require lots more.
    * Collection-specific attributes: a group of humans might require more descriptions
* Should support multiple tasks.
    * Otherwise, what’s the point?

Lessons from SW (specifically games and rendering engines)
* Scenes typically accompanied by 
* Hinton really wants this - see: Capsule Networks

### How do we achieve a readable disentangled representation?
Natural scene de-rendering: latent scheme should take the form of an XML of scene description.
Should learn in an unsupervised way.
Way it was implemented: replace the decoder with a graphics engine!
Problems: learning isn’t very easy.
Black-Box optimization with REINFORCE.

With this symbolic representation, we can solve other problems trivially, like inpainting.
Analogy making: would be very difficult with normal latent representations, but not with symbolic representations!
Image captioning also much easier.
VQA is also simple - you now have a structured database
Can also work with videos, particularly when you pair the symbolic representation with physics engines.

Zero-shot task generalization.
Can you compact symbolic representations for text and speech? He doesn’t know. What form would they take?

Given a task, learn an embedding of the task. Then you can take in observations and choose actions and decide whether you’re finished or not.
Task embedding should be properly disentangled. Encourage this with analogy-making: this prior helps you put structure on the task description itself.

Question: how did you infer symbolic representation for inpainting tasks?

Question: haven’t you outsourced the task of picking symbols to the graphics engine?
* With minimal addition from the designer (just the DSL, basically), you don’t need supervisory labels. Labels emerge themselves if you provide the schema.

Question: input to the graphics enginer?
* Take mish-mash of high D vector data and convert into class object, which is passed directly to graphics engine.

Question: what about environments that don’t have schemas? Can you transfer to places that are different?
* We should be able to transfer schemas - this is the right track.
* We don’t have good generative models for text! NLU community has tried, but they’re not as good as graphics at replicating signals.
* Should go hand-in-hand with the universe of tasks.
