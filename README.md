# AI Talent Salary Predictor

This project trains a salary prediction model on the Global AI Jobs dataset and serves predictions through a Gradio frontend.

## What It Does
- trains Random Forest and XGBoost models
- evaluates both models and selects the better one
- saves the selected model to `models/selected_model.pkl`
- runs a Gradio app that sends inputs through an agent pipeline for ETL, inference, and LLM-based business interpretation

## Main Files
- `Group_1_codes.ipynb`: end-to-end notebook for training and frontend launch
- `skills/`: skill specifications used by the notebook agents
- `models/selected_model.pkl`: saved selected model artifact
- `.env`: stores the OpenAI API key

## Inputs Used
- job role
- experience level
- year of exp
- country
- education
- industry
- company size
- work mode

## Run
1. Add `OPENAI_API_KEY` to `.env`.
2. Open and run `Group_1_codes.ipynb` from top to bottom.
3. Use the Gradio UI to submit inputs and view the salary estimate, interpretation, and pipeline trace.
