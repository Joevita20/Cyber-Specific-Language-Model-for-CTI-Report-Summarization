# A Cyber-Specific Language Model for Cyber Threat Intelligence Report Summarization

---

## Overview

Cybersecurity threats have surged by 67% in the past year alone, creating an urgent demand for intelligent systems capable of processing and summarizing Cyber Threat Intelligence (CTI) reports at scale. This project presents a domain-adapted language model built on the RoBERTa architecture, fine-tuned specifically for the cybersecurity domain to automate CTI report summarization with high accuracy and efficiency.

The model introduces a strategic noise factor during adaptation, enabling it to capture nuanced cybersecurity terminology while retaining compatibility with general English language patterns.

---

## Key Contributions

- A cyber-specific vocabulary built using a byte-level tokenizer, optimized to a 50,256-token vocabulary
- A novel noise-infused weight adaptation strategy applied to shared tokens between the cyber vocabulary and the original RoBERTa vocabulary
- Empirical probability-based vocabulary management to retain critical cybersecurity terms
- Fine-tuning pipeline across Named Entity Recognition (NER), Masked Word Prediction, and Cyberbullying Detection before final CTI report summarization

---

## Model Architecture

The proposed model is built on RoBERTa with the following specifications:

| Component | Details |
|---|---|
| Base Model | RoBERTa |
| Hidden Layers | 12 |
| Attention Heads | 12 |
| Embedding Dimensions | 768 |
| Vocabulary Size | 50,256 |
| Tokenizer | Byte-level BPE |
| Training Hardware | T4 GPUs |
| Batch Size | 12 |

---

## Methodology

**Step 1 — Build Cyber Vocabulary**  
Common tokens between the custom cyber vocabulary and the RoBERTa vocabulary are identified and assigned the same indices. New cybersecurity-specific tokens are assigned random indices, with empirical probability used to manage the final vocabulary size.

**Step 2 — Adapt RoBERTa**  
Noise drawn from a normal distribution N(μ, σ) is introduced to the pretrained weights of shared tokens, allowing the model to learn cybersecurity-specific nuances without losing general language understanding.

**Step 3 — Fine-Tune**  
The adapted model is progressively fine-tuned on NER, masked word prediction, and cyberbullying detection tasks, before final fine-tuning on CTI report summarization.

---

## Tasks

- Named Entity Recognition (NER) — identifying cybersecurity entities such as threat actors, vulnerabilities, and attack vectors
- Masked Word Prediction — domain-specific language understanding
- Cyberbullying Detection — evaluating contextual classification capability
- CTI Report Summarization — the primary downstream task

---

## Technologies

- Python
- PyTorch
- HuggingFace Transformers
- RoBERTa
- T4 GPUs

---

## Results

The model demonstrates strong performance across all fine-tuning tasks, with the noise-infused adaptation enabling effective capture of cybersecurity-specific language patterns. The final model provides a promising solution for automated CTI report summarization, bridging the gap between general-purpose language models and the specialized requirements of threat intelligence analysis.

---

