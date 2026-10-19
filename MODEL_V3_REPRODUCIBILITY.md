# Model v3 reproducibility

## Dataset construction

| Item | Value |
|---|---:|
| Data type | Synthetic behavioural data |
| Synthetic users | 600 |
| Generated days per user | 60 |
| Labelled user-days | 31,800 |
| Historical feature window | D−7 to D−1 |
| Target day | D |

Each labelled example uses seven complete historical local days for features and the subsequent prediction day for the target.

## Train and held-out split

| Item | Value |
|---|---:|
| Split unit | Synthetic user |
| Training users | 480 |
| Held-out users | 120 |
| Training observations | 25,440 |
| Held-out observations | 6,360 |
| Held-out share | 20% of users |

The user-level split prevents overlapping histories from an individual synthetic user appearing in both subsets.

## Model configuration

| Item | Value |
|---|---|
| Model type | Binary Logistic Regression |
| Model version | v3 |
| Optimisation | Full-batch gradient descent on L2-regularised log loss |
| Learning rate | 0.5 |
| Iterations | 1,500 |
| L2 regularisation | 0.001 |
| Random seed | 20261007 |
| Missing numerical values | Frozen training-mean imputation |
| Standardisation | Training-set mean and population standard deviation |

## Artefact identity

SHA-256:

`8205a15ec89d4ad288f00d109718e3e81ff0a4298fb4011ce662e59e8a9e6885`

## Reproducibility limitations

The fixed configuration supports reproducibility of the synthetic experiment, but it does not remove its methodological limitations. Synthetic data assumptions influence both inputs and outcomes. Reproducible synthetic metrics therefore do not demonstrate real-world predictive validity, causal effects or generalisability.

This public repository intentionally excludes application source code, private repository paths, participant data, credentials and database content.
