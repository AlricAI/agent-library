# Fix

> Diagnose and fix bugs with architecture-aware analysis and diagnostic-first approach

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Bug Diagnosis and Fix Command

Intelligently diagnose and fix bugs by:
1. **Adding diagnostic instrumentation** to capture current behavior
2. **Deep architecture analysis** using `/docs/architecture/data-model.md`
3. **Hypothesis generation** (5-7 possible sources, distilled to 1-2 most likely)
4. **User confirmation** before implementing fix
5. **Root cause documentation** for cross-project memory

## Current Bug Report
**User Input:** `$ARGUMENTS`

Please diagnose and fix the bug described above using the complete workflow outlined in this document.

## Command Usage

```bash
/fix "payment processing fails for subscriptions"
/fix "null pointer error in user service"
/fix "UI not updating after API call"
```

## Execution Flow

```mermaid
flowchart TD
    START[User Reports Bug] --> CHECK{data-model.md exists?}
    CHECK -->|No| GEN[Generate data-model.md]
    CHECK -->|Yes| READ[Read architecture docs]
    GEN --> READ
    
    READ --> CONTEXT[Gather bug context]
    CONTEXT --> LOGS[Add diagnostic logs/instrumentation]
    
    LOGS --> REPRODUCE[Attempt to reproduce bug]
    REPRODUCE --> ANALYZE[Analyze log output]
    
    ANALYZE --> HYPOTHESIS[Generate 5-7 hypotheses]
    HYPOTHESIS --> DISTILL[Distill to 1-2 most likely causes]
    
    DISTILL --> VALIDATE[Validate with diagnostic data]
    VALIDATE --> PRESENT[Present diagnosis to user]
    
    PRESENT --> CONFIRM{User confirms diagnosis?}
    CONFIRM -->|No| LOGS
    CONFIRM -->|Yes| FIX[Implement fix]
    
    FIX --> TEST[Test fix thoroughly]
    TEST --> VERIFY[Verify bug resolved]
    
    VERIFY --> CLEANUP[Remove diagnostic logs]
    CLEANUP --> DOCS[Document root cause]
    DOCS --> MEMORY[Write to cross-project memory]
    
    MEMORY --> COMPLETE[✅ Bug Fixed]
    
    style START fill:#fbb,stroke:#333,stroke-width:2px
    style COMPLETE fill:#bfb,stroke:#333,stroke-width:2px
    style CONFIRM fill:#ffb,stroke:#333,stroke-width:2px
```

## Phase 1: Context Gathering & Architecture Analysis (

*[truncated — see source for full prompt]*