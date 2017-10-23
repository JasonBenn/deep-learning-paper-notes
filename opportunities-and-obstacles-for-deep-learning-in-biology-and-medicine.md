## [Opportunities And Obstacles For Deep Learning In Biology And Medicine](https://www.biorxiv.org/content/early/2017/05/28/142760)

_May 2017_

> "Genomics alone will equal or surpass data generation by social media and online video within the next decade"

---

tldr: after a first pass, these are the particularly interesting papers that I'd want to explore further:

1b Electronic Health Records
81, 82: DeepPatient. Denoising autoencoders can create useful reprs of patients, huge for insurance. But no data.

1c Challenges/opportunities In Patient Categorization
92: Can reduce reliance on expert review w semi/un-supervised or "anchor and learn" framework (rely on high confidence observations to infer labels).

2e MiRNA
185, 186: Some success with RNNs on sequences.

2f Protein Folding
27, 199, 200: Contact map prediction: harder than ^ but much better for tertiary structure prediction. Some success with 2D RNNs.

2g Morphological Phenotypes
16,202,203: Image analysis via segmentation super successful.

3a Clinical Decision Making
268: representations of causal relationships
269: clinical time series NN, analyzed hidden neurons for causality

3b Drug Repositioning
35: "most promising piece of work" but a proof-of-concept.

3c Drug Development
Interesting representations of chemical compounds: 308, 309.
311: One-shot learning to infer representations for new tasks with just 1-10 examples.
312, 313: datasets
316: atomic convolutions: future potential for modeling protein structure.
314, 324: representations for chemicals useful for generating compounds, like how word2vec is useful for NLP tasks.

4b Interpretation
168, 177, 333: Occluding/changing parts of input, observing change.
335: Backprop to input layer
344: Visualizing hidden representation
352: Attention on DNA
353: attention for EHR
365: GAN that produces "rationales" - what?! Beat attentional method.

4e Data, Code, And Model Sharing
313: DeepChem, open source approaches to drug discovery, compared.

---

# Detailed notes

## 1. Categorize
DL is good for classifying disease/disease subtypes, esp cancers. Some signals are in molecular data, some are by counting "mitotic divisions" in histological images, etc. Experts can only do so much.

### 1a Imaging Applications:
* Often <1M examples to train from, but pretraining/transfer learning from natural images has worked.
* MRIs have very little data. Data augmentation worked.
* Be careful with overconfident predictions. Better to reduce coverage.
* Chest X-rays categorized using weak labels (NLP-extracted keywords from radiology reports associated with images) got 90% F-measure, nice.
* TLDR: tricky. Generally fewer but larger images, poor annotations. Data augmentation/transfer learning/weak labeling more needed. Also, recall/precision tradeoff important.
* Software for combining experts w DL would be great.

### 1b Electronic Health Records
* Tons of free text. Nobody's beaten SOTA domain-specific approaches yet with DL yet.
* NLP < DL NLP for extracting pathology info (primary site, laterality of tumors)
* Medical word2vec exists, but hard to evalute how good it is.
* 81, 82: DeepPatient. Denoising autoencoders can create useful reprs of patients, huge for insurance; but plagued by data integration problems.

### 1c Challenges/opportunities In Patient Categorization
* Many medical data sets require expert review, thus, they're tiny. Getting anonymized data critical.
* 92: Can reduce reliance on expert review w semi/un-supervised or "anchor and learn" framework (rely on high confidence observations to infer labels).
* Unrefined data is the new oil - look for refining techniques! Complement, not replace, expert review.
* Challenges:
* EHRs are unstandardized.
* Privacy laws restrict use -> take analysis to data.
* "Right to an explanation" introspectability will be key
* Longitudinal studies are seq proc tasks!

## 2. Study
* DL is good for fundamental biology research. Could be good at parsing massive amounts of DNA data, for example. Can "predict gene targets of microRNAs" 26.
* Massive potential to change our understanding of disease in future. Esp. unsupervised techniques.

### 2a Gene Expression

* RNA data falling in price and sample sizes increasing. Denoising autoencoders useful for identifying RNA proteins for cell processes and grouping things by nominal or mutated! Be wary of overinterpreting tho, a lot of groups have mysterious purpose.
* RBMs: used to define ovarian cancer subtypes from epigenetic data.
* Future is bright.


### 2b Splicing

* Genes have coding regions (exons) interspersed with noncoding regions (introns). Pre-mRNA has both, and splicing removes the introns. This mechanism leads to great power (can create many proteins from one gene) and great opportunity for mutations.
* Goal: individualized diagnostics/therapies by identifying the mutations that cause mis-splicing.
* Some success with clever sources of data (linear model with a "hexamer motif frequencies" feature), has outperformed DL.
* Lymphocyte: white blood cell
* Lymphoblast: undifferentiated lymphocyte


### 2c Transcription Factors And Rna

* TFs regulate gene expression. Goal is to predict their attachment sites.
* ChIP-seq identifies highly likely binding sites.


### 2d Epigenomics

* Epigenetics: lots of heritable changes don't involve changes in the genome: DNA methylation (attachment of methyl groups to DNA that can repress transcription), histone modification (proteins that affect how DNA is folded), etc.
* Gene: DNA sequence for a protein.
* Gene expression: transcription (creating RNA copy of some DNA), RNA processing sometimes (splicing of eukaroytic genes into mRNA), translation (RNA base pair triplets AKA codons are used by ribosomes to chain together amino acids, which match up to codons), folding, translocation, transport (by the Golgi apparatus).
* Promoter: sequence at the head of a gene that triggers transcription.
* Transcription regulation via enhancers/promoters is poorly understood, as enhancers could be 1M base pairs away.
* Goal: identify transcription regulators in DNA. Some success with CNNs.
* We're gonna need to get really good at large-scale attentional models.


### 2e MiRNA

* Predicting microRNA and their targets (gene regulation) currently relies on lots of feature selection. Interesting because it's critical for gene regulation and preserved across great evolutionary distance.
* 185, 186: Some success with RNNs on sequences.
* Already useful IRL: "Further incremental advances in deep learning for miRNA and target prediction will likely be sufficient to meet the current needs of systems biologists and other researchers who use prediction tools mainly to nominate candidates that are then tested experimentally"


### 2f Protein Folding

* Understanding structure of protein critical for bio and drug development, but only 100k solved structures in Protein Data Bank (out of 94M sequences in UniProt). Many subproblems.
* Secondary structure prediction:
* 27, 199, 200: Contact map prediction: harder than ^ but much better for tertiary structure prediction. Some success with 2D RNNs.
* Key: capturing long-range sequential info (researchers have tried doing so with convolutions).
* Unclear if DL methods generalize to proteins without sequence homologs (i.e., similar sequences because of same genetic ancestor)


### 2g Morphological Phenotypes

* 16,202,203: Image analysis via segmentation super successful.
* "Recent work by Johnson et al. [207] demonstrated how the use of a http://dx.doi.org/10.1101/142760 conditional adversarial autoencoder allows for a probabilistic interpretation of cell and nuclear morphology and structure localization from fluorescence images. The proposed model is able to generalize well to a wide range of subcellular localizations"


### 2h Single-cell Data


### 2i Metagenomics

* Study of genetic material from microbial communities.


### 2j Sequencing And Variant Calling


## 3 Treating Disease
* DL is good for treatment as the body is a complex system. Predicting drug interactions, protein folding, etc.
* Think: personalized healthcare, precision medicine.
* Goals:
* 1: improve patient intervention choices
* 2: develop new interventions


### 3a Clinical Decision Making

* Problems for DL: easier to predict an outcome than to suggest an action to change the outcome; predicting an outcome is less useful. Also: interpretibility is critical and difficult with DL.
* Goal: recast clinical decision-making problem as decision problem.
* 268: representations of causal relationships
* 269: clinical time series NN, analyzed hidden neurons for causality
* 223: "impressive application of DL to other domains... relied on knowledge of the underlying processes"
* 276: by accurately classifying patients as pre-dementia, helped reduce clinical trial sample size by 5x.


### 3b Drug Repositioning

* Cool! Drugs are expensive to create, so try reusing existing ones instead! Great fit for DL, but mature tool missing.
* Goal: predict therapeutic uses from 288: gene- and pathway-level drug profiles dataset.
* 35: "most promising piece of work" but a proof-of-concept.


### 3c Drug Development

* Goal: identify small molecules that enhance/inhibit disease-relevant biological mechanisms. Molecules must be evaluted on a variety of traits, ranked, studied.
* 2012 Merck Molecular Activity Challenge.
* Interesting representations of chemical compounds: 308, 309.
* Challenge: transfer learning is limited when tasks are different - you need different compound representations.
* 311: One-shot learning to infer representations for new tasks with just 1-10 examples.
* 312, 313: datasets.
* 318, 319: "docking program" to model complex protein structure.
* 316: atomic convolutions: future potential for modeling protein structure.
* Can also generate active compounds by simulating design-synthesize-test cycle.
* 314, 324: representations for chemicals useful for generating compounds, like how word2vec is useful for NLP tasks.
* GANs for molecules.


## 4 Obstacles/opportunities


### 4a Evaluation

* Problems with identifying targets in 3B base pair human genome: class imbalance.
* Labels might come from unreproducible experiments.
* Advice: track the false discovery rate for some tasks. For example, validation experiments for specific biochemical activity needs FDR of 5-25%.
* Classification labels are often arbitrary... applied once a continuous value passes a threshold.


### 4b Interpretation

* People want to understand breakthrough results, and it builds trust. Also, you could be making judgments based on bias in data (a model predicted that pneumonia death risk decreased for patients with asthma... but that's because those ppl were high pri for hospital).
* 168, 177, 333: Occluding/changing parts of input, observing change.
* 335: Backprop to input layer
* 344: Visualizing hidden representation
* 352: Attention on DNA
* 353: attention for EHR
* 365: GAN that produces "rationales" - what?! Beat attentional method.


### 4c Data Limitations

* Impacted all applications.
* Works today: simulating transcription factor binding sites or injecting mutations into real data to make synthetic dataset.
* 371: Diet Networks for reducing # of parameters?


### 4d Hardware Limitations And Scaling

* 398: DL in distributed environment library


### 4e Data, Code, And Model Sharing

* Partly a cultural problem - researchers hoard data.
* 177, 258, 312: provided data preprocessing code.
* 313: DeepChem, open source approaches to drug discovery, compared.


### 4f Multimodal, Multi-task, And Transfer Learning
