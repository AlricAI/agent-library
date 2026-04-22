# Llm Evaluation

> Measure before you ship.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LLM Evaluation Patterns

Measure before you ship. Intuition about model quality is unreliable — score it systematically. This guide covers evaluation frameworks, golden datasets, regression testing, and production monitoring for LLM-powered features.

---

## Why Eval Matters

LLMs are non-deterministic. A prompt change that feels like an improvement can:

- Fix one case and regress five others
- Improve average score while degrading the worst-case
- Pass a vibe check but fail real user queries

Evaluation makes quality changes verifiable and reversible.

---

## Evaluation Stack

```
Layer 1: Automated metrics     — instant, cheap, run on every PR
Layer 2: LLM-as-judge          — nuanced, scalable, no human annotation
Layer 3: Human preference      — ground truth for alignment decisions
Layer 4: Production monitoring — real distribution, real failures
```

Don't skip layers — use all four, at appropriate frequency.

---

## Layer 1: Automated Metrics

### Text Generation

| Metric      | Formula                     | Best for                      |
| ----------- | --------------------------- | ----------------------------- |
| ROUGE-L     | LCS overlap with reference  | Summarization, extraction     |
| BLEU        | n-gram precision            | Translation, templated output |
| BERTScore   | Embedding cosine similarity | Semantic equivalence          |
| Exact Match | char-exact equality         | Structured output, QA         |

**Thresholds for production:** ROUGE-L > 0.4, BERTScore F1 > 0.85

### Code Generation

- **Pass@K**: does any of K samples pass the test suite?
- **Execution Accuracy**: does the output run without errors?
- **BLEU-code**: syntactic similarity to reference solution

### Structured Output

- **Schema Validity**: does the output conform to the expected schema?
- **Field Accuracy**: are individual fields correct? (per-field F1)

---

## Layer 2: LLM-as-Judge

Use a capable model (e.g., Claude Opus, GPT-4o) to score outputs on defined rub

*[truncated — see source for full prompt]*