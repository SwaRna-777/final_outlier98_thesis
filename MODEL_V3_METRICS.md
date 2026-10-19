# Model v3 metrics

## Evaluation context

All results in this document were measured on 6,360 held-out synthetic observations from 120 synthetic users excluded from training. They are not real-user performance results.

## Classification metrics

| Metric | Exact value | Rounded value |
|---|---:|---:|
| Positive-class rate | 0.389623 | 0.390 |
| Majority-class baseline accuracy | 0.610377 | 0.610 |
| ROC-AUC | 0.878483 | 0.878 |
| Accuracy | 0.802673 | 0.803 |
| Precision | 0.759660 | 0.760 |
| Recall | 0.721953 | 0.722 |
| F1 score | 0.740327 | 0.740 |
| Log loss | 0.432822 | 0.433 |
| Brier score | 0.137641 | 0.138 |

The classification threshold was 0.5.

## Confusion matrix

| Actual / predicted | Predicted low execution | Predicted not low execution |
|---|---:|---:|
| Actual low execution | True positive = 1,789 | False negative = 689 |
| Actual not low execution | False positive = 566 | True negative = 3,316 |

## Risk-band calibration

| Risk band | Probability range | Samples | Mean predicted probability | Observed low-execution rate |
|---|---|---:|---:|---:|
| Low | 0.00 to <0.40 | 3,674 | 0.1366 | 0.1418 |
| Medium | 0.40 to <0.70 | 1,138 | 0.5620 | 0.5791 |
| High | 0.70 to 1.00 | 1,548 | 0.8188 | 0.8385 |

## Concise interpretation

The model ranked synthetic low-execution and non-low-execution observations effectively under the synthetic generator assumptions and exceeded the synthetic majority-class baseline. The reported calibration values indicate that mean predicted probability and observed synthetic outcome frequency were close within the three defined bands.

These findings are technical evidence about the synthetic pipeline only. They do not establish real-world predictive accuracy or causal behavioural effects.
