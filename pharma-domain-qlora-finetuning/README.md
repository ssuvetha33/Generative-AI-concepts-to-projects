# Pharma Domain QLoRA Fine-Tuning (Notebook-First Project)

This project keeps the **exact same notebook workflow** for non-instruction (continued pretraining / domain adaptation) fine-tuning in the pharma domain.

## Notebook

- Main notebook: `Pharma_Domain_Causal_LM_FineTuning_With_QLoRA.ipynb`
- Approach: causal language modeling on raw pharma text (not instruction/chat tuning)
- Base model used in notebook: `TinyLlama/TinyLlama-1.1B-intermediate-step-1431k-3T`

## LoRA Adapter (Hugging Face)

Your uploaded adapter repo:

- https://huggingface.co/ssuvetha/pharma-tinyllama-domain-lora

## Project Structure

```text
pharma-domain-qlora-finetuning/
├─ Pharma_Domain_Causal_LM_FineTuning_With_QLoRA.ipynb
├─ README.md
├─ requirements.txt
└─ .gitignore
```

## Setup

1. Create and activate a Python environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Start Jupyter and open the notebook:

```bash
jupyter notebook
```

## Notes for Running

- The notebook currently includes Colab-specific steps (`google.colab`, Drive mount, and userdata token access).
- If running locally in VS Code/Jupyter, replace token retrieval with environment variables:
  - `HF_TOKEN_READ`
  - `HF_TOKEN_WRITE`
- Keep secrets out of git. Use local environment variables.

## Reproducibility and Safety

- This is **educational research code** for domain adaptation.
- Outputs are not medical advice and should not be used for diagnosis or treatment decisions.
- Validate generated content with domain experts before any downstream use.

## Push This Folder to GitHub

From inside this folder:

```bash
git init
git add .
git commit -m "Add pharma QLoRA notebook project"
git branch -M main
git remote add origin <your-github-repo-url>
git push -u origin main
```
