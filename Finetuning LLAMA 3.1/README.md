# Fine-tuning LLAMA 3.1

This repository contains a Python notebook for fine-tuning the LLAMA 3.1 model using the Unsloth library. LLAMA 3.1 is a highly efficient and powerful language model designed for various natural language processing tasks. The notebook leverages advanced techniques and configurations to optimize the fine-tuning process.

## Features of LLAMA 3.1

LLAMA 3.1 excels in:
- Natural language understanding
- Text generation
- Contextual conversation
- Language translation
- Sentiment analysis

## Fine-tuning Techniques Used

The following techniques and configurations are utilized in the fine-tuning process:

1. **Loading Model and Dataset**:
   - Model: `unsloth/Meta-Llama-3.1-8B`
   - Support for various pre-quantized 4-bit models to reduce memory usage and enhance performance

2. **Unsloth Library**:
   - Installing `unsloth` along with `xformers`, `trl`, `peft`, `accelerate`, and `bitsandbytes`

3. **Model Configuration**:
   - Sequence length: `max_seq_length = 2048`
   - Data type detection: `dtype = None` (auto-detection)
   - 4-bit quantization: `load_in_4bit = True`

4. **Supported 4-bit Models**:
   - `unsloth/Meta-Llama-3.1-8B-bnb-4bit`
   - `unsloth/Meta-Llama-3.1-8B-Instruct-bnb-4bit`
   - `unsloth/Meta-Llama-3.1-70B-bnb-4bit`
   - `unsloth/Meta-Llama-3.1-405B-bnb-4bit`
   - `unsloth/Mistral-Nemo-Base-2407-bnb-4bit`
   - `unsloth/Mistral-Nemo-Instruct-2407-bnb-4bit`
   - `unsloth/mistral-7b-v0.3-bnb-4bit`
   - `unsloth/mistral-7b-instruct-v0.3-bnb-4bit`
   - `unsloth/Phi-3-mini-4k-instruct`
   - `unsloth/Phi-3-medium-4k-instruct`
   - `unsloth/gemma-2-9b-bnb-4bit`
   - `unsloth/gemma-2-27b-bnb-4bit`

5. **PEFT Configuration**:
   - LoRA (Low-Rank Adaptation) configuration:
     - `r = 16`
     - Target modules: `["q_proj", "k_proj", "v_proj", "o_proj", "gate_proj", "up_proj", "down_proj"]`
     - LoRA alpha: `lora_alpha = 16`
     - LoRA dropout: `lora_dropout = 0`

## Getting Started

To run the notebook, ensure you have the required libraries installed. You can install them using:

```bash
pip install "unsloth[colab-new] @ git+https://github.com/unslothai/unsloth.git"
pip install --no-deps "xformers<0.0.27" "trl<0.9.0" peft accelerate bitsandbytes
