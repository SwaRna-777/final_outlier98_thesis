# Outlier98 – Model v3 Data Analysis and Evaluation

This repository contains supporting Data Science analysis for the Outlier98 MSc project. It documents Model v3, an interpretable binary Logistic Regression model that estimates next-day low-execution risk.

The repository contains analysis and evaluation documentation only. The Outlier98 application source code, participant-level private data, database exports, credentials, and personal records are not publicly included.

## Navigation

| Document | Contents |
|---|---|
| [Model analysis](MODEL_V3_ANALYSIS.md) | Objective, target, feature window, preprocessing and interpretation |
| [Metrics](MODEL_V3_METRICS.md) | Held-out synthetic metrics, confusion matrix and calibration |
| [Features](MODEL_V3_FEATURES.md) | Definitions of the nine model features |
| [Reproducibility](MODEL_V3_REPRODUCIBILITY.md) | Dataset, split, configuration and artefact identity |
| [Results summary](RESULTS_SUMMARY.md) | Concise examiner-facing result summary |
| [Limitations](LIMITATIONS.md) | Methodological limits and appropriate interpretation |

## Model summary

| Item | Value |
|---|---|
| Model | Binary Logistic Regression |
| Version | v3 |
| Target | `next_day_low_execution` |
| Feature window | Seven complete local days: D−7 to D−1 |
| Prediction-day behaviour | Excluded from features |
| Synthetic users | 600 |
| Labelled user-days | 31,800 |
| Train / held-out observations | 25,440 / 6,360 |
| Train / held-out users | 480 / 120 |
| Split | User-level |

Low execution is defined as completion of less than 50% of eligible planned activity on prediction day D. Planned activity consists of active Habits, due Tasks and scheduled T-Blocks. Partial Habit completion contributes 0.5 only during target construction. Days with no planned activity have no target label.

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

## Configuration and artefact

Training used full-batch gradient descent with learning rate 0.5, 1,500 iterations, L2 regularisation of 0.001 and random seed `20261007`.

Model artefact SHA-256:

`8205a15ec89d4ad288f00d109718e3e81ff0a4298fb4011ce662e59e8a9e6885`

## Reproducible analysis

| Resource | Description |
|---|---|
| [notebooks/Model_V3_Data_Analysis.ipynb](notebooks/Model_V3_Data_Analysis.ipynb) | Executable Model v3 Data Science analysis |
| [data/model_v3_synthetic_dataset.csv](data/model_v3_synthetic_dataset.csv) | Synthetic behavioural dataset used for Model v3 |
| [MODEL_V3_ANALYSIS.md](MODEL_V3_ANALYSIS.md) | Modelling methodology |
| [MODEL_V3_METRICS.md](MODEL_V3_METRICS.md) | Evaluation results |
| [MODEL_V3_FEATURES.md](MODEL_V3_FEATURES.md) | Feature definitions |
| [MODEL_V3_REPRODUCIBILITY.md](MODEL_V3_REPRODUCIBILITY.md) | Reproducibility information |

The dataset is synthetic and contains no real participant information.

## Interpretation boundary

All reported predictive-performance values are held-out synthetic results. They show technical behaviour of the modelling pipeline under the assumptions of the synthetic generator. They do not establish real-world predictive validity, causal effects, or population-level generalisability.

The synthetic generator introduces structural circularity because outcomes are partly generated using related behavioural assumptions. Feature contributions are linear model explanations, not causal effects.
