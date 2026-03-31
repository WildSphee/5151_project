---
name: model_selection
description: Compare the results of two models and select the better one and give the reason
mode: LLM-driven
---

# Model Selection Skill

## When to use
- User asks to compare two models
- User wonders which model performs better in prediction
- User wants to choose a better model from candidate models

## How to execute
- Receive the evaluation metrics (RMSE, MAE, and R2) of the two models from ModelAgentState
- Compare the metrics and select the model with a lower RMSE, a lower MAE, and a higher R2
- If the three metrics have conflicts, choose the model with a lower RMSE
- Store the selected model and reason as selected_model and selection_reason in ModelAgentState
- Tell the user which model is better and provide its evaluation metrics

## Input from agent state
- random_forest_evaluation_metrics: dict
- xgboost_evaluation_metrics: dict

## Output to agent state
Store the selected model and reason as selected_model and selection_reason in ModelAgentState

## Output format
Always return output in json format {"selected_model": selected_model, "model_name": model_name, "selection_reason": reasoning}
- selected_model is either random_forest_model or xgboost_model
- model_name is either "Random Forest" or "XGBoost"
- reasoning is a string starting "[model_name] performs better because ...", followed by the comparison of evaluation metrics, such as a lower RMSE, or a higher R2

## Constraints
- reasoning should not exceed 150 words total
- Use plain, accessible language
- Get the evaluation metrics from evaluation agents. Do not use fake numbers