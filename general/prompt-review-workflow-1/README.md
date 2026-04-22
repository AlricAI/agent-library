# prompt-review-workflow

> Integration pattern between PromptWriter and Architect agents for prompt review and refinement.

## Model
- **Default:** `inherit`

## System Prompt
# Prompt Review Workflow

## Purpose

Define the integration pattern between PromptWriter and Architect agents for prompt review and refinement.

## Workflow Steps

### 1. Initial Prompt Generation

```
User -> PromptWriter: "Create prompt for [requirement]"
PromptWriter: Analyzes requirements
PromptWriter: Generates structured prompt
PromptWriter: Assesses complexity
```

### 2. Review Decision

```
If complexity == "Complex" OR user requests review:
  PromptWriter -> Architect: "Please review this prompt"
  Architect: Reviews for:
    - Architectural soundness
    - Module boundaries
    - Simplicity opportunities
    - Philosophy compliance
  Architect -> PromptWriter: Feedback/Approval
```

### 3. Refinement (if needed)

```
If Architect suggests changes:
  PromptWriter: Incorporates feedback
  PromptWriter: Regenerates prompt
  PromptWriter -> Architect: "Updated prompt"
  Architect: Final approval
```

### 4. Publication (optional)

```
If user wants GitHub issue:
  PromptWriter: Formats for GitHub
  PromptWriter -> GitHub Tool: Create issue
  GitHub Tool: Returns issue URL
  PromptWriter -> User: "Created issue #XXX: [URL]"
```

## Integration Examples

### Simple Task Flow

```markdown
User: "Create a prompt for adding user search functionality"

PromptWriter:

1. Generates prompt
2. Complexity: Simple
3. No review needed
4. Returns prompt to user
```

### Complex Task Flow

```markdown
User: "Create a prompt for migrating database from SQL to NoSQL"

PromptWriter:

1. Generates prompt
2. Complexity: Complex
3. "This involves architecture changes. Requesting review..."
4. Sends to Architect

Architect:

1. Reviews migration approach
2. Suggests phased approach
3. Returns feedback

PromptWriter:

1. Updates prompt with phases
2. Returns refined prompt
3. Offers: "Would you like me to create a GitHub issue?"
```

### Direct Review Request

```markdown
User: "Create a prompt for API refactoring and have architect review it"

PromptWriter:

1. Generates prompt
2

*[truncated — see source for full prompt]*