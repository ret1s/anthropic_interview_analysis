<h1 align="center">Anthropic Interviewer Analysis</h1>

![Anthropic Interviewer Analysis banner](anthropic_interview_analysis_banner.png)

Lightweight workspace for exploring the public `Anthropic/AnthropicInterviewer` dataset from Hugging Face. The notebook loads all three splits (workforce, creatives, scientists), inspects basic stats, surfaces TF-IDF keywords, and uses OpenAI models to extract per-group themes that can be exported to markdown for diagramming.

## Contents
- `notebooks/anthropic_interviewer.ipynb` — main notebook with data loading, stats, TF-IDF, and LLM analysis/export.
- `notebooks/analysis/llm_group_analysis.md` — saved LLM themes per group (generated after running the export cell).
- `.gitignore` — ignores the local venv, checkpoints, editor files, and data outputs.

## Setup
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -q pandas huggingface_hub openai scikit-learn
```
You can also let the notebook’s first cell (`%pip install ...`) handle installs inside an activated venv.

## Run the notebook
```bash
# activate your venv first
jupyter notebook notebooks/anthropic_interviewer.ipynb
```
Notebook steps (in order):
1) Install deps (setup cell).  
2) Load splits via `hf://datasets/Anthropic/AnthropicInterviewer/...` (no token needed).  
3) Inspect head/sample/length stats.  
4) Run descriptive stats + TF-IDF keywords per group.  
5) Set `OPENAI_API_KEY` and run the LLM themes cell (`gpt-4o` by default).  
6) Run the export cell to write `analysis/llm_group_analysis.md`.

## Notes
- Optional cell persists each split locally under `data/` for offline use.
- The markdown export is ready for downstream diagramming or reporting.
