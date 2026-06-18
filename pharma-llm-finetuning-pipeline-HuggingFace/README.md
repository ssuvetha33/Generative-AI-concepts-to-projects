# End-to-End Pharma LLM Fine-Tuning with Hugging Face

This repository demonstrates a complete **multi-stage LLM adaptation workflow** for the pharmaceutical domain using:

- **Hugging Face Transformers**
- **PEFT / LoRA**
- **QLoRA**
- **TRL / DPO**
- **TinyLlama**

The project progressively adapts a general base model into a pharma-focused model through **three stages**:

1. **Non-instruction fine-tuning** on raw pharma text  
2. **Instruction fine-tuning** on pharma instruction-response data  
3. **Preference tuning** with DPO using chosen/rejected responses  

---

## Project Overview

This project is designed to show how to build a domain-adapted and instruction-capable LLM pipeline in stages.

### Stage 1 — Non-Instruction Fine-Tuning
In Stage 1, the model is trained on raw pharmaceutical text extracted from PDF documents.

This teaches the model:

- pharmaceutical vocabulary
- drug names
- biomedical terminology
- scientific writing style
- domain-specific text patterns

At this stage, the model learns **next-token prediction** only.  
It does **not** yet learn to answer user questions.

---

### Stage 2 — Instruction Fine-Tuning
In Stage 2, the Stage 1 merged model is loaded and fine-tuned on structured pharma instruction-response examples.

This teaches the model:

- how to follow instructions
- how to answer pharma-domain questions
- how to generate assistant-style responses

---

### Stage 3 — Preference Tuning with DPO
In Stage 3, the Stage 2 merged model is used for **Direct Preference Optimization (DPO)** with:

- `prompt`
- `chosen`
- `rejected`

This teaches the model to prefer stronger responses over weaker ones.

---

## Full Pipeline

```text
Base model: TinyLlama
   ↓
Stage 1: Non-instruction fine-tuning on raw pharma text
   ↓
Stage 1 LoRA adapter
   ↓
Merge Stage 1 adapter into base model
   ↓
Stage 1 merged pharma-domain model
   ↓
Stage 2: Instruction fine-tuning on pharma instruction-response data
   ↓
Stage 2 LoRA adapter
   ↓
Merge Stage 2 adapter into Stage 1 merged model
   ↓
Stage 2 merged instruction-tuned pharma model
   ↓
Stage 3: Preference tuning with DPO on prompt / chosen / rejected data
   ↓
Stage 3 LoRA adapter
   ↓
Optional final merge
   ↓
Final preference-aligned pharma model
```

---

## Repository Contents

This repository contains notebook and script versions of the workflow, including:

- **Stage 1 non-instruction fine-tuning notebook/script**
- **Stage 2 instruction fine-tuning notebook/script**
- **Stage 3 preference tuning notebook/script**
- **end-to-end combined workflow**
- processed data generation steps
- model saving, merging, and inference examples

---

## Training Stages Summary

| Stage | Training Type | Input Data | Output |
|------|---------------|-----------|--------|
| **Stage 1** | Non-instruction fine-tuning | Raw pharma text | Domain-adapted LoRA adapter |
| **Stage 2** | Instruction fine-tuning | Instruction-response pairs | Instruction-tuned LoRA adapter |
| **Stage 3** | Preference tuning (DPO) | Prompt + chosen + rejected | Preference-aligned LoRA adapter |

### Simple intuition

- **Stage 1** teaches the model to speak pharma language  
- **Stage 2** teaches the model to answer pharma instructions  
- **Stage 3** teaches the model which answers are better  

---

## Hugging Face Adapters

The trained adapters are available on Hugging Face:

### Stage 1 — Non-Instruction LoRA Adapter
- **Model ID:** `ssuvetha/pharma-tinyllama-non-instruction-lora-adapter`
- **Link:** https://huggingface.co/ssuvetha/pharma-tinyllama-non-instruction-lora-adapter

### Stage 2 — Instruction LoRA Adapter
- **Model ID:** `ssuvetha/pharma-tinyllama-instruction-lora-adapter`
- **Link:** https://huggingface.co/ssuvetha/pharma-tinyllama-instruction-lora-adapter

### Stage 3 — DPO LoRA Adapter
- **Model ID:** `ssuvetha/pharma-tinyllama-dpo-lora-adapter`
- **Link:** https://huggingface.co/ssuvetha/pharma-tinyllama-dpo-lora-adapter

---

## Additional Model Artifacts

This workflow can also produce merged models:

### Stage 1
- non-instruction LoRA adapter
- merged Stage 1 pharma-domain model

### Stage 2
- instruction LoRA adapter
- merged Stage 2 instruction-tuned model

### Stage 3
- DPO LoRA adapter
- optional final merged preference-tuned model

---

## Tech Stack

- Python
- Google Colab
- PyMuPDF
- Hugging Face Datasets
- Hugging Face Transformers
- PEFT
- bitsandbytes
- TRL

---

## Example Workflow

### Stage 1
- extract pharma PDF text
- clean and normalize text
- build Hugging Face dataset
- tokenize and pack text into blocks
- fine-tune TinyLlama with LoRA/QLoRA
- save adapter
- merge adapter

### Stage 2
- load pharma instruction dataset
- format instruction-response examples
- tokenize instruction data
- load Stage 1 merged model
- add fresh LoRA adapter
- instruction fine-tune
- save adapter
- merge adapter

### Stage 3
- load preference dataset
- load Stage 2 merged model
- add fresh LoRA adapter
- train with DPO
- save adapter
- optionally merge final model

---

## Notes

- Stage 1 is **domain adaptation**, not chatbot training.
- Stage 2 is where the model learns **instruction-following** behavior.
- Stage 3 is where the model learns **preference alignment**.
- LoRA adapters are used to keep training lightweight and modular.
- Merged models are created when a standalone model is needed for the next stage or deployment.

---

## Use Cases

This repository is useful for learning and demonstrating:

- domain-adaptive continued pretraining
- staged LLM fine-tuning
- LoRA / QLoRA workflows
- instruction tuning
- DPO preference tuning
- practical Hugging Face training pipelines

---

## Disclaimer

This project is for **educational and research purposes**.  
It is **not medical advice** and should not be used for clinical decision-making.

---

## Author

**Ssuvetha**

If you use this repository for your own learning or adaptation experiments, feel free to extend it with:

- larger domain corpora
- better instruction datasets
- stronger preference datasets
- evaluation pipelines
- deployment workflows