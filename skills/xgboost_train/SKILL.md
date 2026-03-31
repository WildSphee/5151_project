---
name: xgboost_train
description: Train an XGBoost Regressor on the preprocessed AI & Data Jobs salary dataset using a fixed train/test split. Deterministic Python, no LLM involved.
tags: [training, xgboost, regression, gradient boosting]
mode: organisational
---

# Model 2 (XGBoost) Training Skill

## Role
This is an organisational skill. Model fitting with fixed hyperparameters is deterministic. The LLM is not involved. The Python code in xgboost_train_agent was written to satisfy this specification.

## When to use
Invoke this skill immediately after preprocess_agent has written X_train, y_train, and feature_columns to agent state. This skill must run before xgboost_eval_agent.
It runs in parallel with random_forest_train_agent and has no dependency on it.

## Specification
1. Read X_train, y_train, and feature_columns from state.
2. Instantiate XGBRegressor(n_estimators=200, learning_rate=0.05, max_depth=6,
   subsample=0.8, colsample_bytree=0.8, random_state=42, tree_method="hist").
3. Fit the model on X_train and y_train.
4. Store the fitted model in state.xgboost_model.

## Inputs
- X_train: pd.DataFrame, one-hot encoded training features from preprocess_agent
- y_train: pd.Series, continuous salary target values for the training split
- feature_columns: list[str], ordered list of feature names after encoding

## Outputs
- xgboost_model: fitted XGBRegressor object

## Output format
xgboost_model is an XGBoost fitted estimator object, ready to be consumed directly by xgboost_eval_agent via state. XGBoost accepts pd.DataFrame inputs natively; no numpy conversion is needed before passing X_train.

## Business context
This stage produces the second candidate model for predicting salary ranges for AI and data roles. Gradient boosting is included as a comparison against Random Forest because it often captures complex non-linear feature
interactions in structured tabular data, which is relevant here given the mix of categorical job attributes driving salary variation.

## Critical Rule
Do not perform any feature engineering or encoding here. All transformations must have been completed by preprocess_agent before this skill runs.