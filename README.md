# 🏥 AlpaCare MedInstruct Assistant

## 📘 Project Overview
**AlpaCare MedInstruct Assistant** is a fine-tuned **medical instruction language model** that provides safe, educational responses to health-related prompts.  
It uses **LoRA/PEFT fine-tuning** on the [`lavita/AlpaCare-MedInstruct-52k`](https://huggingface.co/datasets/lavita/AlpaCare-MedInstruct-52k) dataset to teach a small (<7B) LLM to follow medical-style instructions safely.

> ⚠️ **Disclaimer:** This project is for **educational purposes only** and does **not provide medical advice, diagnosis, or prescriptions**. Always consult a qualified clinician.

---

## 🧠 Model Architecture & Approach
- **Base Model:** `stabilityai/stablelm-tuned-alpha-3b` 
- **Fine-tuning Method:** LoRA (Low-Rank Adaptation) via Hugging Face PEFT
- **Frameworks:** Transformers, PEFT, bitsandbytes, Accelerate
- **Training Environment:** Google Colab (T4/A100 GPU)
- **Safety Measures:**
  - Each model output includes a disclaimer
  - No dosage, prescription, or diagnosis responses
  - Human evaluation by 30+ medically literate reviewers

---
## 🧩 Repository Structure
AlpaCare-MedInstruct-Assistant/
- │
- ├── data_loader.py
- ├── notebooks/
- │ ├── colab_finetune.ipynb 
- │ ├── inference_demo.ipynb 
- │
- ├── REPORT.md
- ├── requirements.txt
- └── README.md
---

## ⚙️ Setup & Installation

### 1️⃣ Clone Repository
```bash
git clone https://github.com/Kashish-044/AlpaCare-Assistant.git
cd AlpaCare-MedInstruct-Assistant
```
## 📂 Dataset Information
- Dataset: lavita/AlpaCare-MedInstruct-52k
- Split: 90% training / 5% validation / 5% testing
- Cleaning: Removed duplicates, filtered incomplete or unsafe entries
- Preprocessing: Used tokenizer from base model for encoding text

## 🚀 How to Run
🔹 Fine-tuning
Open notebooks/colab_finetune.ipynb in Google Colab and run all cells sequentially.
It will:
- Install all dependencies
- Load and preprocess dataset
- Fine-tune model using LoRA
- Save adapter weights via:
```bash
peft_model.save_pretrained("adapters/alpacare-lora")
```
##🔹 Inference
Run `notebooks/inference_demo.ipynb` to test model responses:
```
Prompt: "What should I do for a mild headache?"
Response: "Try hydration, rest, and monitor symptoms. This is educational only — consult a qualified clinician."
```

## 📊 Evaluation
- Human Review: 30+ medically literate evaluators
- Metrics: BLEU, ROUGE, and safety compliance
- Findings: Majority of outputs rated safe, factual, and well-structured

## ⚖️ Limitations
- The model cannot diagnose or prescribe
- Trained only on educational data; may not generalize to clinical decisions
- Limited by dataset coverage and model size (<7B)

## 📚 References
- Hugging Face PEFT
- LoRA: Low-Rank Adaptation Paper
- lavita/AlpaCare-MedInstruct-52k Dataset

