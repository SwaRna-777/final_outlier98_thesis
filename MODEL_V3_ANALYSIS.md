# Model v3 analysis

## Modelling objective

Model v3 estimates the probability of `next_day_low_execution` for a local calendar day D. It is an interpretable binary Logistic Regression prototype that produces a probability and a low, medium or high risk band.

## Target definition

The positive class is assigned when completed eligible planned execution on day D is below 50%.

Planned activity consists of active Habits, due Tasks and scheduled T-Blocks. Completed activity consists of completed Habits, completed due Tasks and completed T-Blocks. Partial Habit completion contributes 0.5 to the target numerator. Days with no planned activity receive no target label.

## Observation window and leakage prevention

For prediction day D, historical features are calculated from the seven complete preceding local days, D−7 to D−1. Prediction-day behavioural outcomes are excluded from the feature vector. This ensures that the outcome being predicted is not used as an input to the same prediction.

## Preprocessing

Numerical features are standardised with frozen training-set means and population standard deviations. Missing or non-finite numerical values are replaced by the relevant frozen training mean before standardisation. Such an imputed value standardises to zero.

Missingness is not interpreted as behavioural zero. For example, no recorded mood observation is not equivalent to a mood rating of zero.

## Feature-engineering approach

The model uses recent Habit completion, due-Task completion, T-Block completion, recorded focus duration, Habit streak, recency of activity, reminder use, mood and weekend context. The nine exact features are listed in [MODEL_V3_FEATURES.md](MODEL_V3_FEATURES.md).

## Why Logistic Regression

Logistic Regression was selected for a transparent binary-risk prototype. It supports deterministic probability scoring and traceable linear feature contributions while retaining a straightforward relationship between standardised inputs and predicted risk.

## Interpretation

For each non-imputed feature, the explanation contribution is:

`coefficient × standardised feature`

The contributions describe how inputs affect the fitted model score. SHAP is not used. These contributions do not establish that a feature causes a behavioural outcome.

## Synthetic-data rationale

Synthetic behavioural data support reproducible development and technical evaluation when sufficiently large genuine longitudinal data are not available. The generator includes assumptions about discipline, momentum, weekend effects, mood, reminder propensity, disengagement and completion behaviour.

## Critical limitations

Training and held-out evaluation use synthetic data. Consequently, the metrics demonstrate technical pipeline performance under generator assumptions, not real-world predictive validity. Because the generator creates both behavioural inputs and related outcomes, it introduces structural circularity.

The analysis does not establish causal effects, clinical significance, population-level generalisability or productivity improvement. An exploratory three-participant real-user evaluation may support feasibility of behavioural-data collection, but it is not statistical validation of Model v3.
