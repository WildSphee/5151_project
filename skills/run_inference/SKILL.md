---
name: run_inference
description: Predict the salary for a given job title, experience level and educational background, using the chosen model by model selection agent.
Use when the user inputs the job requirements and expects a estimated salary
mode: LLM-driven
---

# Run Inference Skill

## When to use
- User wants an estimated salary for a given job title, experience level and educational background
- User requests a recommended salary for a data or AI related job posting
- User wants to know the market rate for hiring a person in a given position

## How to execute
- LLM reads user prompt which contains key features
- Get selected_model from ModelAgentState
- Use the given features to predict the salary using the selected_model

## Input from agent state
- Store the key features into PredictionAgentState
- Get selected_model from models/selected_model.pkl

## Output to agent state
- Store the predicted salary as prediction in PredictionAgentState

## Output format
Always structure your response like this:
- Respond with "Recommended salary for [job title] with [experience level] years of experience and [educational background] is $[salary range]."
- The salary range is calculated by the model prediction with a 10% upper and lower margin

## Constraints
- Use plain, accessible language
- Predicted salary should be from the chosen model
- Never provide fake numbers