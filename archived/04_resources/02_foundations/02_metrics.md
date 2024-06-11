# Machine Learning Metrics

## ROC Curve and AUC

An **ROC curve (receiver operating characteristic curve)** is a graph showing
the performance of a classification model at all classification thresholds. This
curve plots the true positive rate against the false positive rate for a number
of decision thresholds. It summarises the confusion matrices that each threshold
produces.

**True Positive Rate (TPR)** is a synonym for recall or sensitivity [2] and is,
therefore, defined as follows:

$$
\mathrm{TPR} = \frac{\mathrm{TP}}{\mathrm{TP} + \mathrm{FN}}
$$

**False Positive Rate (FPR)** is defined as follows:

$$
\mathrm{FPR} = (1 - \mathrm{specificity}) =  \frac{\mathrm{FP}}{\mathrm{FP} + \mathrm{TN}}
$$

<figure>
  <img src="../../assets/images/roc-curve.svg" alt="ROC curve" width="300" style="display: block; margin-left: auto; margin-right: auto;">
  <figcaption style="text-align: center;"><b>Figure 1:</b> TP vs. FP rate at different classification thresholds.</figcaption>
</figure>

To compute the points in an ROC curve, we could evaluate a logistic regression
model many times with different classification thresholds, but this would be
inefficient. Fortunately, there's an efficient, sorting-based algorithm that can
provide this information for us, called AUC.

## Area Under the ROC Curve (AUC ROC)

AUC measures the entire two-dimensional area underneath the entire ROC curve
(think integral calculus) from (0,0) to (1,1). This gives an aggregate measure
of performance of across all possible classification thresholds.

One way of interpreting AUC is as the probability that the model ranks a random
positive example more highly than a random negative example. For example, given
the following examples, which are arranged from left to right in ascending order
of logistic regression predictions:

<figure>
  <img src="../../assets/images/auc-predictions-ranked.svg" alt="ROC curve" width="600" style="display: block; margin-left: auto; margin-right: auto;">
  <figcaption style="text-align: center;"><b>Figure 2:</b> Predictions ranked in ascending order of logistic regression score.</figcaption>
</figure>

AUC represents the probability that a random positive (green) example is
positioned to the right of a random negative (red) example.

AUC ranges in value from 0 to 1. A model whose predictions are 100% wrong has an
AUC of 0.0; one whose predictions are 100% correct has an AUC of 1.0.

AUC is desirable for the following two reasons:

- AUC is scale-invariant. It measures how well predictions are ranked, rather
  than their absolute values.
- AUC is classification-threshold-invariant. It measures the quality of the
  model's predictions irrespective of what classification threshold is chosen.

However, both these reasons come with caveats, which may limit the usefulness of
AUC in certain use cases:

- Scale invariance is not always desirable. For example, sometimes we really do
  need well calibrated probability outputs, and AUC won’t tell us about that.
- Classification-threshold invariance is not always desirable. In cases where
  there are wide disparities in the cost of false negatives vs. false positives,
  it may be critical to minimize one type of classification error. For example,
  when doing email spam detection, you likely want to prioritize minimizing
  false positives (even if that results in a significant increase of false
  negatives). AUC isn't a useful metric for this type of optimization.

<!-- Add notes from: https://www.youtube.com/watch?v=4jRBRDbJemM&ab_channel=StatQuestwithJoshStarmer -->

## Bibliography

[1]
[Google Developers - Classification: ROC Curve and AUC](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc)
\
[2] [StatQuest with Josh Starmer - ROC and AUC, Clearly Explained!](https://www.youtube.com/watch?v=4jRBRDbJemM&ab_channel=StatQuestwithJoshStarmer)
