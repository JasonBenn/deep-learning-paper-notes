## Medical Machine Intelligence

Where will ML actually make a difference? Three categories, ordered by when they’ll arrive.

We want to accelerate/enable new tech in healthcare, not “disrupt” healthcare.
 
Diagnostics.
* Technical feasibility is there, but real deployment takes time and care.
* Challenges
    * Often regulated as medical device
    * Interpretibility
* Two scenarios in which we can improve diagnostics:
    * Screening. Example: diabetic retinopathy. It’s image classification, so we’re crushing it - already better than human opthamologists.
        * Surprising additional result: was actual able to infer patients age, hemoglobin, BMI, etc by looking at retina - all of which are relevant for heart disease!
    * Assisted-read. Cancer pathology. 1 in 12 breast cancer biopsies is misdiagnosed - because the task is basically impossible, like looking for a needle in the haystack. ML systems can help you find relevant patches. These guys generate a heatmap of suspicious tissues, which are then given to pathologist.
* Conclusion: medical imaging is going well, but other kinds of diagnostics are worth exploring. Needs more attention on communicating back to physician.
 
Care management/decision support (operations)
* Hypothesis: ML can assist in everyday decisionmaking, reducing errors, lowering costs, and improving care quality.
* Forecast: high likelihood of success, but may take decades before smart EHRs are the norm.
* Challenges: enormous.
    * Data portability and inconsistency (it’s worse than you imagine).
        * Google’s solution: put everything in the best open standard (FHIR)
    * Correlation vs causation. Pneumonia in hospital = better outcomes? (Because they were given more care.)
    * Establishing what kind of help providers really need.
    * Rigorous evaluation of clinical value is going to be super hard.
* Yikes: 1 in 4 patients experience an adverse event in a hospital.
* Great! 85%+ of US hospitals use EHRs.
* Bad: most of this data is never used by humans; are idiosyncratic, incomplete, inconsistent. And almost all of them ignore huge amounts of unstructured data.
* Holy shit - talking about synonyms for an ambiguous reference to “levo” and “glucose”-related measurements - a full page of text of things the doctor could have been referring to.
* Word embeddings: disease -> drug make great analogies, just like the classic word embedding example about country -> capital. Awesome!
 
Personalized medicine
* Example: omics inform routine medication prescription (like antidepressants)
* Forecast: this is basically still sci-fi, but it’s irresistible to investigate.
* Challenges are too numerous to mention.
* Many genomics problems can be recast as prediction problems.
* DeepVariant is DL approach that beats non-DL SOTA for identifying genetic variant classification. The point: ML can help in genetics.
* He skipped over most of this section because so many other speakers addressed it.
