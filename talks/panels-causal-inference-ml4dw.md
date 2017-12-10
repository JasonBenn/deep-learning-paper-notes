## Panel on causal inference
 
Question: what exactly is the role of causal inference on ML methods and practice?
* RL always thinks about “what next”. But not always with the same causal reasoning tools. Our data is fundamentally different than the supervised setting - it’s not IID. Mostly for the one decision case rather than the sequential decision case.
* Medical domain is loaded with “what if” questions. “What if I give this drug to this patient?”
* Imagine a setting when you have a good teacher - imitation learning. Not all teachers are good but some are - this is a setting we’re currently working on.
 
## Panel on ML for the Developing World

Question: how can prevent developing world from building infrastructure that developed world already knows results in poor quality?
* Industry often has no incentives to change their ways depending on who they’re selling to - even if their products aren’t needed. But they want to cash in on their investment. Receiving governments need to be smart.
* Another thing I’d like to push for in terms of responsible data collection: give the consumer more agency about what data is being collected. (“This app is collecting this about you”)
Question: what do we do to get this fantastic research into the hands of practitioners?
* “Try to figure out how to sell it. If somebody wants to buy it from you, that means it’s useful.”
* “I don’t think solutions that are doled out are sustainable in the long term.”
Question: what are some of the dangers of ML for the developing world?
* “How can some bad actor misuse the data? There are many possible scenarios - probably elect a clown president”
Question: fundamental ML researchers sometimes focus on e.g. minimization of error. But maybe practitioners care more about distribution of error. Are there any fundamental disconnects?
* “What’s important is to understand the problem space in which you deploy. If often takes multiple iterations to figure it out. I think you often see that MSE is a terrible metric for classifiers. Sometimes we have a technique that works already quite well for most of population - in that case new technique that helps us to address 5% super well would be very valuable.”
Question: can ground truth data for a specific country be shared for other countries?
* “For India, we recently built a model in India and deployed it in Bangladesh
