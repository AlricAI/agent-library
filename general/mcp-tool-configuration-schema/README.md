# MCP TOOL CONFIGURATION SCHEMA

> ## Purpose

Defines the standard schema for describing ANY MCP tool's capabilities, expected advantages, and integration requirements. Enables tool-ag

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MCP Tool Configuration Schema

## Purpose

Defines the standard schema for describing ANY MCP tool's capabilities, expected advantages, and integration requirements. Enables tool-agnostic evaluation framework.

## Schema Definition

### ToolConfiguration

```yaml
# Required Fields
tool_id: string # Unique identifier (lowercase, underscores)
tool_name: string # Human-readable name
version: string # Semantic version (X.Y.Z)
description: string # What the tool does (1-2 sentences)

# Capabilities
capabilities: # List of tool capabilities
  - id: string # Capability identifier
    name: string # Human-readable name
    description: string # What this capability does
    relevant_scenarios: [enum] # Which test categories benefit
    expected_improvement: enum # "faster" | "more_accurate" | "both"
    mcp_commands: [string] # Actual MCP commands this maps to

# Integration
adapter_class: string # Python class name for adapter
setup_required: boolean # Does tool need setup?
setup_instructions: string # How to set up (if required)
health_check_url: string? # Optional health endpoint
environment_variables: dict? # Required env vars

# Evaluation
expected_advantages: # Where we expect improvements
  NAVIGATION: [string] # Expected benefits for navigation
  ANALYSIS: [string] # Expected benefits for analysis
  MODIFICATION: [string] # Expected benefits for modification

baseline_comparison_mode: enum # "with_vs_without" | "before_vs_after"

# Constraints
max_concurrent_calls: int? # Rate limiting
timeout_seconds: int? # Per-call timeout
fallback_behavior: enum? # "fail" | "skip" | "baseline"
```

### Enumerations

```yaml
ScenarioCategory:
  - NAVIGATION # Finding code across files
  - ANALYSIS # Understanding code structure
  - MODIFICATION # Making precise edits

ExpectedImprovement:
  - faster # Reduces time/operations
  - more_accurate # Improves correctness/completeness
  - both # Improves speed AND accuracy

ComparisonMode:
  - with_vs_without # Compare tool-enabled vs

*[truncated — see source for full prompt]*