# Evaluating Classifiers

## Overfitting
- generalization vs. overfitting
- model overfitting
  - training errors
  - generalization errors
- causes
  - dataset has noise (wrong data)
  - lack of samples

## Pruning

## Evaluation
- confusion matrix
|                   | Predicted Class   |
|                   |    +    |    -    |
| ----------------- |:-------:| -------:|
|               | + | f++(TP) | f+-(FN) |
| Actual Class  | - | f-+(FP) | f--(TN) |
- accuracy
  - correct predictions
  - accuracy = (TP + TN) / (TP + TN + FP + FN)
- can be misleading

## Cost Sensitive Evaluation
- precision
  - p = TP / (TP + FP)
  - how often are we correct when we say the instance belongs to the positive class
  - p increases -> false positive decreases
- recall
  - r = TP / (TP + FN)
  - fraction of positive instances we are labeling as positive classes
  - r increases -> false negative decreases
  - more useful

## Other Metrics
- F1 measure
  - 2rp/(r+p)
  - F1 increases -> FP and FN decrease
- Receiver Operating Characteristic (ROC)
  - TP vs FP
