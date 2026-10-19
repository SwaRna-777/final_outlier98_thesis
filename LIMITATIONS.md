# Limitations

## Synthetic training data

Model v3 was trained on synthetic behavioural data. Synthetic data support controlled, reproducible pipeline development but cannot fully represent real-user variability, changing routines, incomplete logging, context or long-term engagement patterns.

## Synthetic held-out evaluation

All published metrics were measured on held-out synthetic users. A user-level split avoids mixing overlapping histories from the same synthetic user across training and evaluation, but it does not transform the experiment into real-world validation.

## Structural circularity

The synthetic generator includes assumptions about discipline, momentum, mood, weekend effects, reminder propensity, disengagement and completion. Since related assumptions influence generated inputs and outcomes, the model may recover structure already embedded in the generator.

## No established real-world predictive validity

The analysis does not establish that Model v3 predicts low execution accurately for real users. Real-world validation would require prospective predictions recorded before the outcome day, defensible outcome labels, sufficient longitudinal data and evaluation on appropriate unseen users or time periods.

## Limited real-user context

An exploratory real-user evaluation involving three anonymised participants may support practical feasibility and behavioural-data collection. It is not a sufficiently large basis for statistical validation, population-level inference or stable performance estimates. Participant-level information is not published here.

## Uneven engagement and missingness

Periods of low activity and missing evidence have different meanings. No recorded activity may reflect genuine inactivity, incomplete capture, unplanned work outside the system or discontinued feature use. Missing behavioural values must not automatically be interpreted as zero.

## Interpretability is not causality

Model explanations use `coefficient × standardised feature`. This explains the direction and magnitude of a feature within the fitted linear model. It does not prove that changing the feature would cause a change in execution.

## More complex models would not solve the data limitation

More complex algorithms may increase modelling flexibility but would not overcome the fundamental absence of sufficiently large, representative and prospective real-user longitudinal data. They may additionally reduce transparency and increase overfitting risk. The principal limitation is data validity and availability, not only model capacity.
