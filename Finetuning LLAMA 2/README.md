# Fine-tuning LLAMA 2

This repository contains a Python notebook for fine-tuning the LLAMA 2 model using various techniques. LLAMA 2 is a powerful language model designed to handle a variety of natural language processing tasks. The notebook leverages libraries such as `transformers`, `peft`, `bitsandbytes`, and `trl` to implement fine-tuning.

## Features of LLAMA 2

LLAMA 2 is a state-of-the-art language model that excels in:
- Natural language understanding
- Text generation
- Contextual conversation
- Language translation
- Sentiment analysis

## Fine-tuning Techniques Used

The following techniques and configurations are utilized in the fine-tuning process:

1. **Loading Model and Dataset**:
   - Model: `NousResearch/Llama-2-7b-chat-hf`
   - Dataset: `mlabonne/guanaco-llama2-1k`

2. **QLoRA Parameters**:
   - LoRA attention dimension: `lora_r = 64`
   - Alpha parameter for LoRA scaling: `lora_alpha = 16`
   - Dropout probability for LoRA layers: `lora_dropout = 0.1`

3. **BitsAndBytes Configuration**:
   - 4-bit precision model loading: `use_4bit = True`
   - Compute dtype for 4-bit models: `bnb_4bit_compute_dtype = "float16"`
   - Quantization type: `bnb_4bit_quant_type = "nf4"`
   - Nested quantization: `use_nested_quant = False`

4. **TrainingArguments Parameters**:
   - Output directory: `output_dir = "./results"`
   - Number of training epochs: `num_train_epochs = 1`
   - Enable fp16/bf16 training: `fp16 = False`, `bf16 = False`
   - Batch size per GPU for training: `per_device_train_batch_size = 4`
   - Batch size per GPU for evaluation: `per_device_eval_batch_size = 4`
   - Gradient accumulation steps: `gradient_accumulation_steps = 8`
   - Gradient checkpointing: `gradient_checkpointing = True`
   - Learning rate: `learning_rate = 2e-4`
   - Weight decay: `weight_decay = 0.05`
   - Logging steps: `logging_steps = 10`
   - Save strategy: `save_strategy = "epoch"`
   - Evaluation strategy: `evaluation_strategy = "epoch"`
   - Save total limit: `save_total_limit = 1`

5. **Training Loop**:
   - Utilizing `SFTTrainer` from the `trl` library to manage the fine-tuning process.

## Getting Started

To run the notebook, ensure you have the required libraries installed. You can install them using:

```bash
pip install accelerate==0.21.0 peft==0.4.0 bitsandbytes==0.40.2 transformers==4.31.0 trl==0.4.7
