---

name: xgboost_evaluation_model
description: Evaluate XGBoost model using RMSE, MAE, R² and visualizations
---

# XGBoost Evaluation Skill

## When to use
Execute after xgboost_train_agent has completed training.

## How to execute
It is the similar process to the random forest evaluation, but for XGBoost.

1. Load trained model from state.xgboost_model
2. Predict on the hold-out test set X_test (NOT the training set)
3. Calculate RMSE, MAE, R²
4. Generate scatter plot (predicted vs actual)
5. Generate residual plot
6. Use GPT-4o-mini to interpret metrics in plain English that HR can easily undertand
7. Store the evaluation metrics in state.xgboost_evaluation_metrics

## Inputs from agent state
- xgboost_model: Trained model
- X_test: Test features
- y_test: True test salaries

## Outputs to agent state
- xgboost_evaluation_metrics: dictionary with 'rmse', 'mae', 'r2'
- Messages: Plain English interpretation from GPT
- Update state message with evaluation summary

## Output format
Metrics example:
{
    'rmse': 1234.56,
    'mae': 1234.56,
    'r2': 0.1234
}