# AGENT EVALUATION METHODS

> ## Source: 30+ papers from 2024-2026 on learning/teaching/self-improvement evaluation

---

## Priority 1: Quick Wins for Our Harness

### 1. Pre-test

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Evaluation Methods: Research Summary

## Source: 30+ papers from 2024-2026 on learning/teaching/self-improvement evaluation

---

## Priority 1: Quick Wins for Our Harness

### 1. Pre-test Baseline for Teaching (Normalized Learning Gain)

- Run student on questions BEFORE teaching to establish true baseline
- NLG = (post - pre) / (max - pre) -- gold standard from education research (Hake 1998)
- Harvard RCT (Kestin 2025): NLG > 0.7 = high gain
- Add to teaching_eval.py

### 2. Backward Transfer for L6 (Catastrophic Forgetting)

- After update phase, re-test L1 questions
- BWT = score_on_L1_after_L6 - score_on_L1_immediately
- Catches catastrophic forgetting from continual learning literature

### 3. Teaching Dialogue Quality Rubric (Pauzi 2025, GuideEval 2025)

- 4 dimensions: mistake remediation, scaffolding, guidance, elicitation
- LLM-as-judge on teaching transcript
- Add TeachingDialogueGrade to teaching_eval.py

## Priority 2: Medium Effort

### 4. Transfer Score (Near vs Far Transfer)

- Near: same topic, novel questions (we have this)
- Far: same REASONING PATTERN, different domain (we need this)
- Transfer Score = far_transfer_score / near_transfer_score

### 5. Bloom's "Create" Level

- Agent generates novel analysis from learned material
- "Predict which country leads 2030 based on 2026 trends"
- Tests highest cognitive level

### 6. Output Diversity Tracking

- In parallel runs, measure answer variance
- Low diversity + high accuracy = robust
- Low diversity + low accuracy = stuck

## Priority 3: Deeper Integration

### 7. IRT Question Calibration (MetaBench ICLR 2025)

- 2-parameter logistic model on question difficulty/discrimination
- Drop low-information questions, replace with higher-signal ones

### 8. Knowledge Graph Traversal Tests

- Multi-hop retrieval: "connection between Klaebo and Norway's standing?"
- Tests graph RAG quality directly

### 9. Self-Improvement Loop Metric

- Run teaching eval 3x sequentially
- Measure whether teaching 

*[truncated — see source for full prompt]*