# Raft

> +++
date = '2025-02-19T14:48:58Z'
draft = false
title = 'RAFT: Reward rAnked FineTuning - A New Approach to Generative Model Alignment'
categories = [

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
+++
date = '2025-02-19T14:48:58Z'
draft = false
title = 'RAFT: Reward rAnked FineTuning - A New Approach to Generative Model Alignment'
categories = ['RAFT', 'CLIP', 'RLHF', 'fine-tuning']
tag = ['RAFT', 'CLIP', 'RLHF', 'fine-tuning'] 
+++

## Summary

This post is an explanation of this paper:[RAFT: Reward rAnked FineTuning for Generative Foundation Model Alignment](https://arxiv.org/abs/2304.06767).

Generative foundation models, such as **Large Language Models (LLMs)** and **diffusion models**, have revolutionized AI by achieving human-like content generation. 
However, they often suffer from
1. Biases – Models can learn and reinforce societal biases present in the training data (e.g., gender, racial, or cultural stereotypes).
2. Ethical Concerns – AI-generated content can be misused for misinformation, deepfakes, or spreading harmful narratives.
3. Alignment Issues – The model’s behavior may not match human intent, leading to unintended or harmful outputs despite good intentions.

Traditionally, **Reinforcement Learning from Human Feedback (RLHF)** has been used to align these models, but RLHF comes with stability and efficiency challenges.
To address these limitations, **RAFT (Reward rAnked FineTuning)** was introduced as a more stable and scalable alternative. RAFT fine-tunes models using a **ranking-based approach** to filter high-reward samples, allowing generative models to improve without complex reinforcement learning setups.

---

## **Reinforcement Learning from Human Feedback (RLHF)**  

**RHLF** is a technique used to fine-tune AI models by incorporating **human preferences** to improve their responses.  
It helps align AI-generated content with human expectations, making it safer, more reliable, and useful.

### **How RLHF Works**  

1. **Pretraining the Model** 
   * The AI model (e.g., GPT) is first trained using massive amounts of text data (unsupervised learning).    
2. **Collecting Human Feedback**
   * Humans provide feedback on multiple AI-ge

*[truncated — see source for full prompt]*