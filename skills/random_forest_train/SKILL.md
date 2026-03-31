---
name: random_forest_train
description: Train a Random Forest Regressor on the preprocessed AI & Data Jobs salary dataset using a fixed train/test split. Deterministic Python, no LLM involved.
tags: [training, random forest, regression, sklearn]
mode: organisational
---

# Model 1 (Random Forest) Training Skill

## Role
This is an organisational skill. Model fitting with fixed hyperparameters is deterministic. The LLM is not involved. The Python code in random_forest_train_agent was written to satisfy this specification.

## When to use
Invoke this skill immediately after preprocess_agent has written X_train, y_train, and feature_columns to agent state. This skill must run before random_forest_eval_agent.
It runs in parallel with xgboost_train_agent and has no dependency on it.

## Specification
1. Read X_train, y_train, and feature_columns from state.
2. Instantiate RandomForestRegressor(n_estimators=200, min_samples_leaf=4,
   random_state=42, n_jobs=-1).
3. Fit the model on X_train and y_train.
4. Store the fitted model in state.random_forest_model.

## Inputs
- X_train: pd.DataFrame, one-hot encoded training features from preprocess_agent
- y_train: pd.Series, continuous salary target values for the training split
- feature_columns: list[str], ordered list of feature names after encoding

## Outputs
- random_forest_model: fitted RandomForestRegressor object

## Output format
random_forest_model is a scikit-learn fitted estimator object, ready to be consumed directly by random_forest_eval_agent via state. The field name itself identifies the model type for downstream agents and the
Gradio interface.

## Business context
This stage produces the first candidate model that will ultimately predict salary ranges for AI and data roles. The output feeds directly into the evaluation and selection stages, which together determine which model
a hiring manager or job seeker sees results from in the final interface.

## Critical Rule
Do not perform any feature engineering or encoding here. All transformations must have been completed by preprocess_agent before this skill runs.