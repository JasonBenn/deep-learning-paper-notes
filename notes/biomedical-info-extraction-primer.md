#### Key points:

* NER is more difficult in biomedical text. "Heart attack" and "myocardial infarction" are synonyms, for example, and proteins can be described in one of several formats.
* Abbreviations are also difficult and context-dependent. RA could be any of "right atrium", "rheumatoid arthiritis", "renal artery", or more.
* The field used to be heavily reliant on manual feature engineering - an old relation extraction technique simply relied on 8 regexes - but is being turned upside down by deep learning.

#### Things I didn't know

* NELL: Never Ending Language Learner: continually crawl documents looking for correlated terms. Relies on seeds in each category. Ambiguities like the ones mentioned above are troublesome and cause semantic drift - feature engineering and preprocessing are necessary for medical datasets.
* Pointwise mutual information: from information theory. If two random variables were independent, we'd expect them to occur together by chance sometimes. If they interact in any way, we'll observe a difference from what we'd expect. A PMI of 0 means they're independent. Two words that score highly together are "Puerto" and "Rico", which have a PMI of 10.
