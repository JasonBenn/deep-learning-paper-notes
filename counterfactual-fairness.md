## Counterfactual Fairness

Entelo: ML recruiting

Intuitive explanation of fairness.

Contributions:
*Metric*: to test if something is fair
*Algorithm*: that trains fair classifiers

Naive approach: fairness through unawareness of sensitive attrs. Problems: unfair influences of e.g., race on GPA (teachers may believe minority students have behavioral issues) or race on LSAT (reflects socioeconomic status)
Next: equality of opportunity by Hardt: ensure we’re equally accurate for different races. But label might be biased: law school success as label might be impacted by lack of minority teachers.
Causal model helps us build better classifiers.

3 step procedure:
1. Compute unobserved vars in causal model: (like law knowledge)
2. Make change (change race from black to white)
3. Recompute the biased features
Determine that classifier is fair if the counterfactual result is the same as original result.

This approach: compare individual to diff version of herself.
Other approaches: Compares different individuals with same observed features.

For classifiers: train them only on unobserved variables. This guarantees that your model will be counterfactually fair. Requires building casual models.

examples:
* If you suspect that address would be predictive, but that race contributes to address, you’d want to make race a cause of address.
* 

questions:
* what if you don’t have the full graph?
    * You don’t need a complete graph of causes to derive benefit from this model.

tl;dr: a prediction is fair if it would give you the same prediction in a world in which you were different. 
