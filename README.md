# AI Talent Salary Predictor

This project trains salary models on the Global AI Jobs dataset and serves predictions through a Gradio frontend backed by a small agent pipeline.

## Flow
- preprocess the dataset with the approved business inputs only
- train Random Forest and XGBoost
- evaluate both models and select the better one
- save the selected model to `models/selected_model.pkl`
- run Gradio for ETL, inference, and LLM-based business interpretation

## Inputs
- job role
- experience level
- year of exp
- country
- education
- industry
- company size
- work mode

## Files
- `Group_1_codes.ipynb`: end-to-end notebook
- `skills/`: agent skill specs
- `models/selected_model.pkl`: saved selected model artifact
- `.env`: OpenAI API key

## Notes
- the notebook regenerates the `SKILL.md` files from its in-notebook `SKILL_SPECS` dictionary
- the Gradio form uses editable dropdowns and shows a pipeline trace alongside the prediction

## Run
1. Add `OPENAI_API_KEY` to `.env`.
2. Run `Group_1_codes.ipynb` top to bottom.
3. Open the Gradio app and submit a profile.
