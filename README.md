# Model Evaluation: The Curve, and What It Cannot Tell You

## Objective

I evaluated imbalanced classification models and showed why model choice depends on uncertainty, operating thresholds, and the costs of prediction errors.

## Methodology

- Simulated 8,000 cases with 11.8% positives in the test data.
- Evaluated logistic regression with ROC and precision-recall curves.
- Compared logistic regression with gradient-boosted trees.
- Used 500 paired bootstrap samples to measure uncertainty in their performance difference.
- Selected a threshold using expected costs on the training data.
- Compared both models across cost ratios from 2:1 to 50:1.
- Wrote `roc_point()` to calculate one point on a model’s ROC curve.

## Key Findings

The logistic model had a ROC AUC of 0.8468 and average precision of 0.4651, compared with a boosted-model AUC of 0.8431. Their AUC difference was 0.0038, with a 95% interval from −0.0020 to 0.0094, so the test data did not establish that either model was better.

With a missed positive costing ten times a false alarm, the selected threshold was 0.0905. It produced a cost of 0.4692 per case, compared with 0.9437 at the default threshold of 0.5. At the selected threshold, the false-positive rate was 0.296 and the true-positive rate was 0.823.
