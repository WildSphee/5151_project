---
name: preprocess
description: Prepare the AI & Data Jobs salary dataset for model training with deterministic cleaning, one-hot encoding, and a fixed train/test split.
tags: [preprocessing, data ingestion, train-test split, encoding]
mode: organisational
---

# Preprocess Skill

## When to use
Invoke this skill immediately after ingestion_agent has loaded the raw dataframe into state.raw_df.

## Specification
1. Read the raw dataframe from state.raw_df.
2. Separate salary_usd as the regression target.
3. Drop identifier columns that should not be used for training.
4. Fill missing categorical values with 'Unknown' and numeric values with the median.
5. One-hot encode categorical columns using pandas.
6. Create a deterministic train/test split with random_state=42.
7. Store processed_df, X_train, X_test, y_train, y_test, and feature_columns back into ModelAgentState.