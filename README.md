

# 🧠 Finetuning Large Language Models with Unsloth
Overview
This guide outlines the streamlined process for finetuning large language models (LLMs) using the Unsloth library, featuring both the Qwen 2 7B and CodeGemma 7B models. It covers setup, data preparation, training, inference, model saving, logging, and deployment optimizations tailored for resource-constrained environments.

## 🧰 Unsloth Library
Unsloth is designed to accelerate and optimize LLM finetuning by:
- Leveraging kernel and memory management optimizations
- Enabling low-bit quantization (e.g., 4-bit) to minimize hardware load
- Supporting PEFT (Parameter-Efficient Fine-Tuning) adapters for efficient adaptation

### ⚙️ Setup
The workflow starts by installing critical libraries like unsloth, bitsandbytes, accelerate, peft, trl, and datasets. These dependencies empower low-resource finetuning, quantization, and transformer training. The installation is optionally suppressed using notebook magic commands to keep logs clean and readable.

## 📦 Model Loading and PEFT Configuration
Two models—Qwen 2 7B and CodeGemma 7B—are loaded using Unsloth's FastLanguageModel interface. Core details:
- Models are loaded with 4-bit quantization for memory efficiency.
- PEFT adapters are integrated to support parameter-efficient training.
- Unsloth’s loading methods ensure fast initialization and lower resource usage.

### 📝 Data Preparation
The finetuning dataset (yahma/alpaca-cleaned) is processed via:
- A custom prompt-formatting function combining instruction, input, and expected output.
- The insertion of an end-of-sequence token (EOS_TOKEN) to mark completion.
- Mapping the dataset to match LLM input formats, enabling prompt-based training.

### 🚀 Training
Finetuning begins by configuring training hyperparameters such as batch size, learning rate, and number of epochs. Unsloth’s memory-efficient training pipeline ensures high throughput even on limited GPU environments. This step adapts pretrained weights to your dataset and task.

### 🔍 Inference
Post-training, the model can be used to generate predictions and completions based on instruction-style prompts. This validates how well the model has internalized the task-specific patterns.

### 💾 Model Saving
After training, the finetuned model is saved locally or on cloud storage. Saving includes both core weights and adapter configurations (in case PEFT is used), making future reuse and deployment easy.

📊 WandB Logging
Weights & Biases (WandB) integration is used to:
- Monitor training loss and metric trends in real time
- Compare performance across experiments
- Maintain reproducibility through config tracking and visualization

## 🧠 CodeGemma 7B Finetuning
Separate finetuning routines are outlined for CodeGemma, following the same workflow but accounting for model-specific loading and PEFT configurations. This ensures consistent training quality across different LLM architectures.

### 🧩 Merging and Quantization
After finetuning:
- PEFT adapters are merged back into the base model.
- Quantization (like 4-bit or 8-bit) is applied to reduce model size and boost runtime performance. These steps prepare the model for deployment in environments like mobile apps or edge devices.

## 🔗 Colab Notebook
You can view and run the complete notebook at: https://colab.research.google.com/drive/1XTETt9ZmcZc_Kuo-logdgK8G3ivO2Fm1


