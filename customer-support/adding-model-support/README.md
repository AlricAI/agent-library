# Adding Model Support

> Adding model support to Chatbook ranges from minimal (2 files, ~20 lines) to substantial (6+ files, 150+ lines) depending on how the model differs from existing defaults.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How to Add Support for a New Model

Adding model support to Chatbook ranges from minimal (2 files, ~20 lines) to substantial (6+ files, 150+ lines) depending on how the model differs from existing defaults.

The core idea: Chatbook classifies models into **families** and resolves their capabilities through a **hierarchical settings table**. Adding support means (a) teaching Chatbook to recognize the model and (b) telling it how the model behaves.

For a real-world example of a simple addition, see [PR #1355](https://github.com/WolframResearch/Chatbook/pull/1355) (Gemini 2/3 support, 2 files, 21 lines). For a complex addition requiring structural changes, see [PR #1120](https://github.com/WolframResearch/Chatbook/pull/1120) (Claude 3.7 Sonnet improvements, 7 files, 151 lines). For a detailed walkthrough covering new settings, on-demand prompts, formatting fixes, and pipeline reordering, see [Case Study: Adding GPT 5.4 Support](model-support-examples/gpt-5-4.md).

---

## Key Concepts

### Model Families

A model **family** is a string identifier (e.g., `"GPT5"`, `"Claude4"`, `"Gemini2"`) that groups related model variants. Families are the primary key for looking up model-specific settings.

Families are defined in `Source/Chatbook/Models.wl` via `chooseModelFamily0` rules:

```wl
chooseModelFamily0[ wordsPattern[ { "GPT", "5.1", ___ } ] ] := "GPT51";
chooseModelFamily0[ wordsPattern[ { "GPT", "5", ___ } ] ]   := "GPT5";

chooseModelFamily0[ wordsPattern[ { "Claude", "3", ___ } ] ]                        := "Claude3";
chooseModelFamily0[ wordsPattern[ { "Claude", "Haiku"|"Sonnet"|"Opus", "4", ___ } ] ] := "Claude4";

chooseModelFamily0[ wordsPattern[ { "Gemini", "2", ___ } ] ] := "Gemini2";
chooseModelFamily0[ wordsPattern[ { "Gemini", "3", ___ } ] ] := "Gemini3";
```

The `wordsPattern` helper (`Common.wl`) performs a **case-insensitive word boundary match**. The list form `{ "Gemini", "2", ___ }` matches model names like `"gemini-2-flash"`, `"Gemini 2 Pro"`, etc.

*[truncated — see source for full prompt]*