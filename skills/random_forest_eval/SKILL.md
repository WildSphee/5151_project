---

name: random_forest_evaluation_agent
description: Evaluate the Random Forest model performance using regression metrics (RMSE, MAE, and R²) and visualizations.
mode: LLM-assisted
tags: [evaluation, random forest, regression
---

## When to use
Execute after random_forest_train_agent has completed training.

## How to execute
1. Load trained model from state.random_forest_model
2. Predict on the held-out test set (X_test)
3. Calculate the metrics:
   - RMSE: measure the average deviation between predicted and actual values.
   - MAE: measure the average absolute difference between predicted and actual values.
   - R²: measure the proportion of variance in the target variable that is explained by the model.
4. Generate scatter plot (predicted vs actual)
5. Generate residual plot showing errors acrocss salary range
6. Use GPT-4o-mini to interpret metrics in plain English for non-technical stakeholders (HR)
7. Store the evaluation metrics in state.random_forest_evaluation_metrics

## Inputs from agent state
- random_forest_model: Trained model
- X_test: Test features
- y_test: True test salaries

## Outputs to agent state
- random_forest_evaluation_metrics: dict with 'rmse', 'mae', 'r2'
- Messages: Plain English interpretation

## Output format
Metrics example:
{
    'rmse': 15234.56,
    'mae': 12045.23,
    'r2': 0.7623
}

## Notes
- Use the TEST set only, do not evaluate the train data
- GPT-4o-mini promot: "Explain what RMSE, MAE, and R² mean in the context of salary prediction accuracy. Keep in mind that the audiance is an HR"