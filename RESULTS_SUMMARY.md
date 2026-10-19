# Results summary

## Objective

Model v3 estimates the probability that eligible planned execution on the next local calendar day will be below 50%.

## Dataset and model

The experiment used 600 synthetic users with 60 generated days each, producing 31,800 labelled user-days. The model was a binary Logistic Regression model using nine historical features from D−7 to D−1. The user-level split produced 25,440 training observations from 480 users and 6,360 held-out observations from 120 users.

## Main held-out synthetic results

| Metric | Value |
|---|---:|
| ROC-AUC | 0.878 |
| Accuracy | 0.803 |
| Majority-class baseline accuracy | 0.610 |
| Precision | 0.760 |
| Recall | 0.722 |
| F1 score | 0.740 |
| Log loss | 0.433 |
| Brier score | 0.138 |

## Calibration

| Band | Predicted | Observed |
|---|---:|---:|
| Low | 0.137 | 0.142 |
| Medium | 0.562 | 0.579 |
| High | 0.819 | 0.839 |

## Key conclusion

The held-out synthetic results indicate that the model pipeline can learn and score the structured relationships represented in the synthetic dataset. The reported performance and calibration are not evidence of real-world predictive validity.

## Main limitation

The synthetic generator encodes behavioural assumptions related to the model inputs and outcomes. This structural circularity limits the extent to which synthetic performance can be generalised to genuine user behaviour.
