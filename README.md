# Fine-Tuning-LLMs

This repository contains code and resources related to Fine-Tuning Large Language Models (LLMs) for various natural language processing tasks.

## Explanation about LoRA, QLoRA, and DoRA

### LoRA (Low-Rank Adaptation)

LoRA is an efficient adaptation approach designed to address the challenge of fine-tuning large language models (LLMs) with a vast number of parameters. Traditional full fine-tuning becomes less feasible as LLMs grow in size, as it requires retraining all model parameters, leading to significant computational costs. LoRA introduces trainable rank decomposition matrices into each layer of the Transformer architecture, effectively reducing the number of trainable parameters for downstream tasks. This approach significantly decreases GPU memory requirements and training time while maintaining or even surpassing the performance of traditional fine-tuning methods.

### QLoRA (Quantized LoRA)

QLoRA builds upon the efficiency of LoRA by further reducing memory usage without sacrificing task performance. By backpropagating gradients through a frozen, 4-bit quantized pretrained language model into Low-Rank Adapters (LoRA), QLoRA achieves remarkable memory savings while preserving full 16-bit fine-tuning task performance. The Guanaco model family, trained using QLoRA, outperforms previous models on various benchmarks, showcasing the effectiveness of this approach. QLoRA introduces innovative techniques such as 4-bit NormalFloat (NF4) data type and Double Quantization to optimize memory usage further.

### DoRA (Weight-Decomposed Low-Rank Adaptation)

DoRA is a novel parameter-efficient fine-tuning method that aims to bridge the accuracy gap between full fine-tuning and methods like LoRA and its variants. It decomposes the pre-trained weight into magnitude and direction components for fine-tuning, leveraging LoRA for directional updates. By enhancing both the learning capacity and training stability of LoRA, DoRA achieves superior performance without incurring additional inference overhead. Experimental results demonstrate that DoRA consistently outperforms LoRA on fine-tuning tasks across various downstream tasks.
