# Model v3 features

For prediction day D, historical features use the seven complete preceding local calendar days, D−7 to D−1. Prediction-day outcomes are excluded.

| Feature | Behavioural meaning | Historical window | Role in model | Missing-value handling |
|---|---|---|---|---|
| `habit_completion_rate_7d` | Done Habit-days divided by active Habit-days | D−7 to D−1 | Recent Habit completion consistency | Missing where no active Habits exist; imputed with frozen training mean |
| `task_completion_rate_7d` | Completed eligible due Tasks divided by eligible due Tasks | D−7 to D−1 | Recent due-Task execution | Missing where no eligible due Tasks exist; imputed with frozen training mean |
| `tblock_completion_rate_7d` | Completed scheduled T-Blocks divided by scheduled T-Blocks | D−7 to D−1 | Planned focus-block execution | Missing where no T-Blocks were scheduled; imputed with frozen training mean |
| `avg_focus_mins_7d` | Average recorded finished focus-session duration per day | D−7 to D−1 | Recent recorded focus activity | Zero-focus days remain part of the seven-day average |
| `current_streak` | Consecutive qualifying Habit days ending on D−1 | Ending at D−1 | Habit-engagement continuity | Zero when no qualifying prior streak exists |
| `days_since_last_active` | Days from D to the latest prior recorded activity | Before D | Activity recency | Capped at 14 days where necessary |
| `reminder_usage_rate` | Created Tasks with reminders divided by created Tasks | D−7 to D−1 | Reminder configuration behaviour | Missing where no Tasks were created; imputed with frozen training mean |
| `avg_mood_7d` | Mean logged mood rating on a 1–5 scale | D−7 to D−1 | Available self-reported mood context | Missing where no mood is logged; imputed with frozen training mean |
| `is_weekend` | Whether day D is Saturday or Sunday | Prediction day D | Calendar context | Never missing; 1 for weekend, 0 otherwise |

## Important interpretation rules

`habit_completion_rate_7d` uses Done Habit-days in its numerator. Partial Habit completion is not equivalent to Done for this feature. Partial completion contributes 0.5 only during target construction.

Focus is based on recorded focus-session duration, not planned T-Block duration. Missing data must not automatically be interpreted as behavioural zero. Where an input is missing, the model uses the frozen training mean rather than inventing a zero value.
