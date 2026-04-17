<div align="center">


# **Translating Classic Hindi Literature into English using NLP/GenAI**

**Fine-Tuning Helsinki MarianMT (`opus-mt-inc-en`) with Samanantar + LaBSE Quality Filtering**

![Project Banner](https://github.com/yourusername/hindi-nmt-premchand/raw/main/assets/banner-devanagari-english.png)

[![Kaggle Notebook](https://img.shields.io/badge/▶_Run_on_Kaggle-0357A5?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/code/aviral-kumar-goyal/helsinki-nlp-opus-mt-inc-en-samanantar-dapt)  
[![Hugging Face Model](https://img.shields.io/badge/🤗_Hugging_Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co/Helsinki-NLP/opus-mt-inc-en)  
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org/)  
[![License MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)  
[![MNIT Jaipur](https://img.shields.io/badge/MNIT_Jaipur-0066CC?style=for-the-badge)](https://www.mnit.ac.in/)


</div>

---

### ✨ **The Transformation (Report Highlights)**

**From cold 12.01 SacreBLEU → poetic 15.77 SacreBLEU**  
**+3.76 absolute | +31.3% relative improvement** in **just one DAPT epoch** on 150,000 quality-filtered pairs.

- **Outperforms every Helsinki MarianMT variant** (opus-mt-hi-en, opus-mt-mul-en, raw opus-mt-inc-en)
- **Literary gains on Premchand classics**: +3.43 BLEU on *Poos Ki Raat* and +3.93 BLEU on *Do Bailon Ki Katha*
- **Zero extra fine-tuning** — pure **Domain-Adaptive Pre-Training (DAPT)** + **LaBSE** noise removal
- **Runs entirely on free Kaggle dual-T4 GPUs** (≈3–4 hours)

> “A single epoch of thoughtful pre-training can teach a model not just words, but the *soul* of a language.”  
> — Project Report, 2026

---

### 📖 **Project Story (Straight from the Report)**

Hindi, spoken by **over 600 million** people and written in the beautiful Devanagari script, is the official language of India. Yet the majority of global knowledge, scientific literature, and digital content remains in English. This creates a deep linguistic divide.

**This repository solves exactly that.**

We took the mid-tier **Helsinki-NLP/opus-mt-inc-en** (MarianMT encoder-decoder transformer covering the full Indic family) and gave it a **cultural and linguistic upgrade** using:
- The massive **Samanantar corpus** (47.7 million parallel pairs)
- **LaBSE quality filtering** (τ = 0.85) to remove ~15% crawl noise
- **Domain-Adaptive Pre-Training (DAPT)** — treating the diverse corpus as a language-modelling task

The result? A model that finally understands **figurative language, rural idioms, emotional depth, and classical Hindi literature** the way a human reader would.

**Full 14-page academic report** (LaTeX formatted), **complete Kaggle notebook**, and **20-slide presentation** are included.

---

### 🛠️ **End-to-End Pipeline (Exactly as in Report Section 3.6)**

```mermaid
flowchart LR
    A[📦 Raw Samanantar<br>47.7M pairs] --> B[🔍 LaBSE Quality Filter<br>cosine ≥ 0.85]
    B --> C[✨ 150K High-Quality Pairs]
    C --> D[🔄 DAPT on Helsinki<br>opus-mt-inc-en<br>1 epoch • LR=5e-5 • Adafactor • FP16]
    D --> E[📊 Fixed IIT Bombay Test<br>3,000 pairs]
    E --> F[📖 Premchand Literary Eval<br>Poos Ki Raat + Do Bailon Ki Katha]
    F --> G[🚀 Inference<br>Beam=12 • len_penalty=0.6 • no-repeat-ngram=3]
