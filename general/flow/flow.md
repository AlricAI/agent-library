---
name: Flow
description: ```mermaid
flowchart TD
  A["UserPrompt(initial_prompt)"]
  B["LLMPrompt(llm_prompt)"]
  C["DSLText(rule_source)"]
  R[("DB:rules+prompts+provenance")
model: claude-sonnet-4-5
---
# Rule Authoring → Execution Flow (v0)

```mermaid
flowchart TD
  A["UserPrompt(initial_prompt)"]
  B["LLMPrompt(llm_prompt)"]
  C["DSLText(rule_source)"]
  R[("DB:rules+prompts+provenance")]
  TT["Templates(template_dsl)"]
  RS[RulesetBuilder]
  RS2[RulesetMetadata]
  P[Parser]
  V["Validator(SchemaRegistry)"]
  K[Compiler]
  E1[Errors_to_UI]
  IR["CompiledIR_JSON(ir.schema.json)"]
  RSIR[("DB:ruleset_version_IR+manifest")]
  L[LoadIR]
  N[Instantiate_RETE_Network]
  Cache[("In_memory_cache")]
  Facts[Incoming_Facts]
  Agenda["Agenda/Refraction"]
  Actions["Emit_Actions/Derived_Facts"]
  Outputs["Decisions/Violations/PayLines"]

  A -->|LLM_interprets| B
  B --> C
  C -->|Store| R
  TT -->|Materialise| C

  subgraph Admin
    TT
  end

  subgraph Tenant_UI
    A --> B
    B --> C
    RS -->|select_tenant_rules| RS2
  end

  RS2 -->|gather_DSLs| P
  P -->|AST| V
  V -->|ok| K
  V -->|errors| E1

  K --> IR
  IR -->|Store| RSIR

  subgraph Orchestrator
    RSIR --> L
    L --> N
    N --> Cache
  end

  Facts --> N
  N --> Agenda
  Agenda --> Actions
  Actions --> Outputs
```

Notes

- Templates are read-only and used to create tenant-owned rules.
- Rules store `initial_prompt`, `llm_prompt`, `llm_model`, but prompts are omitted in standard reads.
- Rulesets compile only tenant rules into a single IR artefact, which the orchestrator loads.