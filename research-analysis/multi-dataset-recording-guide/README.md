# MULTI DATASET RECORDING GUIDE

> ## The Ultimate Vectro Demo

**Duration:** 5-6 minutes  
**Datasets:** SIFT1M (vision) + GloVe (NLP) + SBERT (NLP)  
**Key Message:** Consistent, prod

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🎬 Multi-Dataset Demo - Video Recording Guide

## The Ultimate Vectro Demo

**Duration:** 5-6 minutes  
**Datasets:** SIFT1M (vision) + GloVe (NLP) + SBERT (NLP)  
**Key Message:** Consistent, production-ready performance across diverse embedding types

---

## 🎯 Why Three Datasets?

1. **SIFT1M (128D)** - Classic computer vision benchmark, gold standard for ANN
2. **GloVe (100D)** - Stanford word embeddings, widely recognized in NLP
3. **SBERT (384D)** - Modern sentence embeddings, realistic for RAG/search

**Credibility:** All three are well-known, citable datasets. Shows Vectro works across domains.

---

## 📋 Pre-Recording Setup

```bash
cd /Users/wscholl/vectro

# Ensure dependencies
pip install numpy tqdm

# Make scripts executable
chmod +x demos/run_complete_demo.sh

# Test run (optional - do this before recording!)
./demos/run_complete_demo.sh

# Clean terminal for recording
clear
```

---

## 🎬 Recording Script

### SCENE 1: Introduction (0:00 - 0:30)

**[Clean terminal, start recording]**

> "Hi! Today I'm showing you Vectro - a high-performance vector quantization library written in pure Mojo. But here's what makes this demo special: we're not just testing it with one dataset. We're benchmarking it against three completely different embedding types to prove it works consistently across domains."

**[Pause]**

> "We'll test SIFT1M - that's computer vision descriptors. GloVe - Stanford word embeddings. And SBERT - modern sentence transformers. Let's see if Vectro can handle all three."

---

### SCENE 2: Launch Demo (0:30 - 0:50)

**[Type and run]**

```bash
./demos/run_complete_demo.sh
```

**[While script header appears]**

> "I've created a single script that downloads all three datasets and runs comprehensive benchmarks. Let's watch it work."

**[Show downloading SIFT1M]**

> "First up, SIFT1M - this is the classic vector similarity benchmark from INRIA. 100,000 vectors in 128 dimensions."

---

### SCENE 3: Dataset Downloads (0:50 - 1:30)

**[GloV

*[truncated — see source for full prompt]*