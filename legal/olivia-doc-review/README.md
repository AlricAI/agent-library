# Olivia Doc Review

> ## When To Use

Use this when reviewing a strategic doc, feature spec, or planning artifact for compliance with Olivia's trust model, terminology, str

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Olivia Doc Review

## When To Use

Use this when reviewing a strategic doc, feature spec, or planning artifact for compliance with Olivia's trust model, terminology, structure, and linkage standards.

## Goal

Review a target document against four checks: advisory-only compliance, glossary consistency, information-type separation, and doc linkage integrity.

## Input

- The path to the document to review

## Steps

### 1. Load reference sources

Read:

1. the target document
2. `docs/vision/product-ethos.md`
3. `docs/glossary.md`
4. `docs/strategy/agentic-development-principles.md`
5. `docs/learnings/decision-history.md`

### 2. Run the four checks

#### Check 1: Advisory-Only Compliance

- Flag language that implies Olivia takes consequential action without explicit approval.
- Pay special attention to phrases such as `send`, `execute`, `schedule`, `automatically`, `notify`, `submit`, `delete`, `post`, `run`, `trigger`, or `without approval`.
- For each issue, quote the sentence, explain the trust-model risk, and suggest an advisory-only revision.
- If the doc explicitly marks an approved exception as `ADVISORY EXCEPTION`, treat it as a reviewed exception rather than a violation.

#### Check 2: Glossary Term Consistency

- Compare terminology in the document against `docs/glossary.md`.
- Flag misuse of canonical terms, invented product terms, or wording that conflicts with the advisory-only definition.
- For each issue, quote the term in context, cite the canonical meaning, and recommend the correction.

#### Check 3: Information-Type Separation

- Check whether `Facts`, `Decisions`, `Assumptions`, `Open Questions`, and `Deferred Decisions` are clearly distinguished.
- Flag places where settled and unsettled material are blended together or where a decision, assumption, or open question is buried in unlabeled prose.
- For each issue, quote the passage, identify the information type, and recommend a clearer placement or restatement.

#### Check 4: Doc Linka

*[truncated — see source for full prompt]*