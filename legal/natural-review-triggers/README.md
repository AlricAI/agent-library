# Natural Review Triggers

> ## Purpose

Trigger code reviews at meaningful boundaries that respect developer flow while catching issues when they're easiest to fix.

## Contract


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module: Natural Review Triggers

## Purpose

Trigger code reviews at meaningful boundaries that respect developer flow while catching issues when they're easiest to fix.

## Contract

### Inputs

- **Code Changes**: Current implementation in progress
- **Context State**: Module boundaries, complexity metrics, risk indicators
- **Developer Intent**: What they're trying to accomplish

### Outputs

- **Review Decision**: Whether to trigger review now
- **Review Type**: Quick check vs deep analysis
- **Review Focus**: What specifically to examine

### Side Effects

- May pause implementation for review
- Creates review records in logs
- Updates complexity metrics

## Review Trigger Categories

### 1. Natural Completion Points

**When to trigger**: Code represents a complete thought

```yaml
triggers:
  - module_complete: "Finished implementing a complete module"
  - feature_complete: "Core functionality is working"
  - integration_point: "About to connect to external system"
  - abstraction_layer: "Just created a new abstraction"
```

**Review depth**: Full philosophy and design check

### 2. Complexity Thresholds

**When to trigger**: Complexity signals emerge

```yaml
early_warning_signals:
  - second_abstraction: "Adding 2nd layer of abstraction"
  - third_dependency: "Pulling in 3rd external dependency"
  - nested_depth_3: "Code nesting exceeds 3 levels"
  - multiple_responsibilities: "Function doing more than one thing"

hard_stops:
  - cyclomatic_complexity: "> 10 in single function"
  - file_count: "> 3 files in single feature"
  - coupling: "> 3 modules interdependent"
```

**Review depth**: Focused on simplification opportunities

### 3. Risk-Based Triggers

**When to trigger**: Touching sensitive areas

```yaml
immediate_review:
  - authentication: "Any auth/authz code"
  - file_system: "Direct file manipulation"
  - subprocess: "Spawning external processes"
  - network: "External API calls"
  - data_persistence: "Database/storage changes"
  - secrets: "Anyt

*[truncated — see source for full prompt]*