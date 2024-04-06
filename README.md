# Fine-Tuning-LLMs

This repository contains code and resources related to Fine-Tuning Large Language Models (LLMs) for various natural language processing tasks.

## Explanation about LoRA, QLoRA, and DoRA

### LoRA (Low-Rank Adaptation)

**1. Method Overview:**
LoRA is an efficient adaptation approach designed to address the challenge of fine-tuning large language models (LLMs) with a vast number of parameters. Traditional full fine-tuning becomes less feasible as LLMs grow in size, as it requires retraining all model parameters, leading to significant computational costs. LoRA introduces trainable rank decomposition matrices into each layer of the Transformer architecture, effectively reducing the number of trainable parameters for downstream tasks.

**2. Core Points and Advantages:**
- Reduction in Parameters: LoRA significantly reduces the number of trainable parameters compared to full fine-tuning, making it more feasible for large-scale models.
- GPU Memory Reduction: By reducing the number of parameters, LoRA also reduces the GPU memory requirements for training.
- Performance Preservation: Despite the reduction in parameters, LoRA maintains or even surpasses the performance of traditional fine-tuning methods on various benchmarks.

**3. Example:**
For example, when fine-tuning a model like GPT-3 with 175 billion parameters, deploying independent instances of fully fine-tuned models becomes prohibitively expensive. However, using LoRA, the number of trainable parameters can be reduced by thousands of times, significantly reducing both computational costs and GPU memory requirements.

### QLoRA (Quantized LoRA)

**1. Method Overview:**
QLoRA builds upon the efficiency of LoRA by further reducing memory usage without sacrificing task performance. By backpropagating gradients through a frozen, 4-bit quantized pretrained language model into Low-Rank Adapters (LoRA), QLoRA achieves remarkable memory savings while preserving full 16-bit fine-tuning task performance.

**2. Core Points and Advantages:**
- Enhanced Memory Efficiency: QLoRA introduces innovative techniques such as 4-bit NormalFloat (NF4) data type and Double Quantization to optimize memory usage further.
- Performance Preservation: Despite memory optimizations, QLoRA maintains task performance comparable to full fine-tuning methods.

**3. Example:**
For instance, QLoRA enables fine-tuning a 65-billion-parameter model on a single 48GB GPU while preserving full 16-bit fine-tuning task performance, showcasing its remarkable memory efficiency compared to traditional fine-tuning approaches.

### DoRA (Weight-Decomposed Low-Rank Adaptation)

**1. Method Overview:**
DoRA aims to bridge the accuracy gap between full fine-tuning and methods like LoRA by decomposing the pre-trained weight into magnitude and direction components for fine-tuning, leveraging LoRA for directional updates.

**2. Core Points and Advantages:**
- Enhanced Learning Capacity: By decomposing the weight and leveraging LoRA for directional updates, DoRA enhances both the learning capacity and training stability of LoRA.
- Superior Performance: Experimental results demonstrate that DoRA consistently outperforms LoRA on fine-tuning tasks across various downstream tasks.

**3. Example:**
For example, DoRA consistently outperforms LoRA on fine-tuning tasks such as LLaMA, LLaVA, and VL-BART on various downstream tasks, showcasing its superiority in performance and efficiency.

